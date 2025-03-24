---
title: "How to isolate complex queries in an object oriented fashion"
date: 2016-01-28
categories: 
  - "article"
tags: 
  - "activerecord"
  - "designpattern"
  - "oop"
  - "rails"
  - "ruby"
---

Building complex queries in ruby can make your code quite difficult to read, manage and reuse. In this blog post I'll present a simple method to decorate active record objects to make your queries fun again!

<!--more-->

# The problem

Let's assume we are building a system to search talented football players. A player has the following fields:

```
  ActiveRecord::Schema.define do
    create_table :players do |t|
      t.string :forename
      t.string :surname
      t.date :birth_date
      t.string :role
      t.string :nationality
      t.string :preferred_foot
      t.integer :shoots
      t.integer :goals
      t.integer :assists
      t.integer :passes
      t.integer :successful_passes
      t.string :team_name
    end
  end
```

And the corresponding active record model is the following:

```
class Player < ActiveRecord::Base
  scope :right_foot, -> { where(preferred_foot: 'right') }
  scope :left_foot, -> { where(preferred_foot: 'left') }
end

```

Our application mostly deal with `TalentHunters`, objects whose responsibility is to find good players based on a search criteria. For simplicity let's assume that a search criteria has just three components:

- whether or not the player is part of a big team
- whether or not the player has a good shoot accuracy
- and whether or not the player is young.

Finally let's also assume that our talent hunter only specialise on right foot players. The simplest, fastest implementation we can think is an object that uses the search parameters to build the query using a list of conditional statements. Here is a possible implementation:

```
class TalentHunterWithNaiveQuery
  TOP_TEAMS = ['ac milan', 'real madrid', 'barcelona']
  SHOOT_ACCURACY = 0.7
  MAX_AGE = 25

  def initialize(options)
    @playing_for_top_team = options.fetch(:playing_for_top_team, true)
    @with_young_age = options.fetch(:with_young_age, true)
    @with_great_accuracy = options.fetch(:with_great_accuracy, true)
  end

  def find_good_forward
    scope = Player

    scope = scope.right_foot

    if @playing_for_top_team
      scope = scope.where('team_name IN (?)', TOP_TEAMS)
    else
      scope = scope.where.not('team_name IN (?)', TOP_TEAMS)
    end

    if @with_great_accuracy
      scope = scope.where('goals / shoots > ?', SHOOT_ACCURACY)
    else
      scope = scope.where.not('goals / shoots > ?', SHOOT_ACCURACY)
    end

    if @with_young_age
      scope = scope.where('YEAR(?) - YEAR(birth_date) < ?', Date.today, MAX_AGE)
    else
      scope = scope.where.not('YEAR(?) - YEAR(birth_date) < ?', Date.today, MAX_AGE)
    end

    scope
  end
end

```

I don't think this is necessarily bad. We can refactor it using the Extract Method \[note\]Refactoring using Extract Method\[/note\] or we can possibly creates scopes in the `Player` model to handle the different queries.

Here I'd like to present an alternative which relies on a flavour of the Query Object design pattern \[note\]Query objects in Ruby\[/note\] \[note\]Query objects in Java\[/note\].

# Refactoring

The key idea is to isolate the queries in a separate object without polluting the active record model with scopes. This is because queries like `young`, `with great shoot accuracy` or `playing for a top team` only makes sense when performing the task of talent hunting so it seems natural to keep them separate.

I am a great fan of the decorator pattern \[note\]The decorator pattern\[/note\] to enrich objects functionality for a specific use case. For talent hunting we are looking for some sort of definition of `InterestingPlayer`, that behaves like a `Player` but have some extra scopes to make our querying life easier. Here is an attempt:

```
class InterestingPlayer
  TOP_TEAMS = ['ac milan', 'real madrid', 'barcelona']
  SHOOT_ACCURACY = 0.7
  MAX_AGE = 25

  attr_reader :scope

  def initialize(scope = Player)
    @scope = scope
  end

  def playing_for_big_team
    self.class.new @scope.where('team_name IN (?)', TOP_TEAMS)
  end

  def not_playing_for_big_team
    self.class.new @scope.where.not('team_name IN (?)', TOP_TEAMS)
  end

  def with_great_shoot_accuracy
    self.class.new @scope.where('goals / shoots > ?', SHOOT_ACCURACY)
  end

  def without_great_shoot_accuracy
    self.class.new @scope.where.not('goals / shoots > ?', SHOOT_ACCURACY)
  end

  def young
    self.class.new @scope.where('YEAR(?) - YEAR(birth_date) < ?', Date.today, MAX_AGE)
  end

  def old
    self.class.new @scope.where.not('YEAR(?) - YEAR(birth_date) < ?', Date.today, MAX_AGE)
  end

  def method_missing(method, *args, &block)
    result = @scope.send(method, *args, &block)

    is_a_relation?(result) ? self.class.new(result) : result
  end

  def respond_to?(method, include_private = false)
    super || @scope.respond_to?(method, include_private)
  end

  private

  def is_a_relation?(obj)
    obj.instance_of? relation_class_name
  end

  def relation_class_name
    "#{@scope.name}::ActiveRecord_Relation".constantize
  end
end

```

We can split the methods of this object in two sets. The first set of methods is enriching the `Player` active record model with domain specific queries related to the task of talent hunting. When you call one of the domain specific queries  an object of type `InterestingPlayer` is built and returned immediately, like here:

```
  def playing_for_big_team
    self.class.new @scope.where('team_name IN (?)', TOP_TEAMS)
  end

  def not_playing_for_big_team
    self.class.new @scope.where.not('team_name IN (?)', TOP_TEAMS)
  end

  def with_great_shoot_accuracy
    self.class.new @scope.where('goals / shoots > ?', SHOOT_ACCURACY)
  end

  def without_great_shoot_accuracy
    self.class.new @scope.where.not('goals / shoots > ?', SHOOT_ACCURACY)
  end

  def young
    self.class.new @scope.where('YEAR(?) - YEAR(birth_date) < ?', Date.today, MAX_AGE)
  end

  def old
    self.class.new @scope.where.not('YEAR(?) - YEAR(birth_date) < ?', Date.today, MAX_AGE)
  end
```

The second set of methods is slightly more complicated and it is the one dealing with the delegation. When `InterestingPlayer` receives a method call that does not match with any of its public methods we delegate the call to the underlying scope. At this point couple of things could happen:

- The result is a relation again. In this case we just want to return another instance of \`InterestingPlayer\` to let the user compose his query further.
- The result is not a relation, and so the query object have finished his work and we just want to return the result.

This is how this how it could be implemented:

```
  def method_missing(method, *args, &block)
    result = @scope.send(method, *args, &block)

    is_a_relation?(result) ? self.class.new(result) : result
  end

  def respond_to?(method, include_private = false)
    super || @scope.respond_to?(method, include_private)
  end

  private

  def is_a_relation?(obj)
    obj.instance_of? relation_class_name
  end

  def relation_class_name
    "#{@scope.name}::ActiveRecord_Relation".constantize
  end
```

Finally, let's have a look at how a `TalentHunter` use this query object:

```
class TalentHunterWithQueryObject
  def initialize(options)
    @playing_for_top_team = options.fetch(:playing_for_top_team, true)
    @with_young_age = options.fetch(:with_young_age, true)
    @with_great_accuracy = options.fetch(:with_great_accuracy, true)
  end

  def find_good_forward
    search  = InterestingPlayer.new

    search = search.right_foot
    search = @playing_for_top_team ? search.playing_for_big_team : search.not_playing_for_big_team
    search = @with_great_accuracy ? search.with_great_shoot_accuracy : search.without_great_shoot_accuracy
    search = @with_young_age ? search.young : search.old

    search
  end
end

```

I think this enabled two major results:

- We extracted the domain specific queries into the \`InterestingPlayer\` object, effectively enabling reuse without polluting the general purpose active record model.
- We made the \`find\_good\_forward\` method a bit easier to read because it now only uses domain terms instead of having to translated them into db queries.

# Conclusions

We have seen how to decorate a simple active record model (`Player`) to extract queries related to a specific task into a separate object (`InterestingPlayer`). As a result we simplified the object responsible to build the query and arguably it is now easier to read and comprehend (`TalentHunter`). Code and tests are available on Github.

I'd love to hear your opinion on the comments, or just tweet me your opinion!

# References
