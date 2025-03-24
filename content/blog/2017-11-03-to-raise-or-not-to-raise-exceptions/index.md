---
title: "To raise or not to raise exceptions, and the art of designing return values"
date: 2017-11-03
categories: 
  - "article"
tags: 
  - "ruby"
  - "softwaredesign"
  - "softwareengineering"
---

Each time we call a function that's meant to perform some operation that could succeed or fail we are always left with the same dilemma. What should be the return value? Should I return `nil` if a _failure_ happened? Or I should throw an exception? What does _failure_ means anyway?

Like every interesting question, the answer is _it depends_. In this blog post, I'll bring clarity to the discussion and present what are the tradeoffs involved and how to choose between the existing alternatives.

<!--more-->

Let's start with an example when `nil` might be a good idea.

For that, let's consider the Ruby `Enumerable#find` method \[note\]Ruby enumerable find method\[/note\]. If you never used it before such method is responsible to search a value that satisfies the condition specified in the provided block. If the value can't be found then the method returns `nil` like so:

```
(1..10).find { |i| i == 42 }
=> nil
```

Now let's stop for a second and ponder. Why is `nil` a valid return value for that function? The key idea is that element you are looking for _may or may not be there_. In other words, it _is expected_ that a value may not be found and this is a specific trait of the function we are working on.

Coming up with such expectations is not a trivial job. Even functions with the same name can be interpreted differently. For example let's consider to the ActiveRecord `find` method \[note\]Rails ActiveRecord find method\[/note\]. Same name, different context. Here we don't return `nil` when the object is not found but instead, we raise an exception as follows:

```
begin
  my_record = Record.find(1)
rescue ActiveRecord::RecordNotFound => e
  puts "Could not find record with id 1"
end
```

> Whether or not raising an exception depends on your context and what is commonly perceived as the norm.

But what is it that makes this method different? Here the goal is to find a record in the database given an `id`. The fact that we have a unique identifier at hands entails that the record does exist already and that unless something exceptional occurs we will find it in the database. This is why we raise an exception _if we don't_. Whether or not raising an exception depends on your context and what is commonly perceived as the norm.

But the above discussion goes beyond `nil` versus raising exceptions. In fact being `nil` the billion dollar mistake of our time \[note\]Null References the billion dollar mistake\[/note\] whenever you find yourself leaning towards `nil`  you should spend time seeking for a reasonable fallback instead.

> Whenever you find yourself leaning towards nil  you should spend time seeking for a reasonable fallback.

The `parse` method of the nokogiri gem is a great example for that. When trying to parse a `nil` document the library does not raise an exception and returns a fallback value instead, an empty `HTML::Document` object like so:

```
document = Nokogiri::HTML::Document.parse(nil)
=> #<Nokogiri::HTML::Document:0x3fe82eb44d5c name="document" children=[#<Nokogiri::XML::DTD:0x3fe82eb449c4 name="html">]>
```

Now you can compose such empty document with subsequent operations and get back reasonable values instead of checking for `nil` all the time, like so:

```
Nokogiri::HTML::Document.parse(nil).css('h1')
=> []
```

# No silver bullet, please

From my previous discussion, you might conclude that if you ponder enough about your domain you will always find a good insight that will let you decide whether or not you should raise an exception or if a good fallback value exist. Unfortunately, this is not true and a simple way to demonstrate it is to look at how division by zero works in different languages:

```
i = 3/0
# Ruby, ZeroDivisionError: divided by 0
```

```
var i = 3/0;
// Javascript, returns Infinity
```

```
$i = 3/0
// PHP, returns INF and a warning
```

```
i = 3/0
# Python, ZeroDivisionError: division by zero
```

As you can see, you are not the only one confused here! When every other heuristic fails, the safest bet is to just follow the convention of the codebase. In other words, if under a given context (for example API calls) every other function is raising an exception (for example if the API call fails) then by following the existing convention you respect the Principle of least surprise \[note\]Wikipedia: Principle of least surprise\[/note\] and you will make every other developer in your team happier.

> When every other heuristic fails, the safest bet is to just follow the convention of the codebase

# Conclusion

Return values and `nil` belongs to one of the top 100 answers in StackOverflow and I probably did not give them enough justice in this short blog post so I would invite you to dig deeper, it's a fascinating discussion. \[note\]StackOverflow: Avoiding != null statements\[/note\] \[note\]Should a retrieval method return 'null' or throw an exception when it can't produce the return value?\[/note\]

There is a lot that can be done beyond using `nil` and exceptions, for example with tools like monads or response objects. However, this is a broader topic and I will leave such discussion for a follow-up blog post.

If you are interested in reading more please let me know in the comments and if you enjoyed this blog you can also follow me on twitter.

# References
