---
title: "Introducing Hash#dig_and_collect, a useful extension to the Ruby Hash#dig method"
date: 2016-11-04
categories: 
  - "article"
tags: 
  - "code-design"
  - "ruby"
  - "softwareengineering"
---

In this blog post I will introduce Hash#dig\_and\_collect , a simple utility method that is built on top of Hash#dig to help you navigate nested hashes mixed up with arrays.

<!--more-->

## Why Hash#dig is great

The introduction of the Hash#dig\[note\]Ruby Hash#dig documentation\[/note\] method in Ruby 2.3 completely changed the way I navigate deeply nested hashes. For example, given this Hash :

```
client = {
  details: {
    first_name: "Florentino",
    last_name: "Perez"
  },
  addresses: {
    postcode: "SE1 9SG",
    street: London Bridge St,
    number: 32,
    city: "London",
    location: {
      latitude: 51.504382,
      longitude: -0.086279
    }
  }
}
```

to get the latitude and longitude you need to do the following:

```
client[:addresses] && client[:addresses][:location] && client[:addresses][:location][:latitude]
```

which is not only weird, but also verbose. Since Ruby 2.3 you can finally write:

```
client.dig(:addresses, :location, :latitude)
```

which is, needless to say, awesome. However, I started wondering if it was possible to stretch the idea of Hash#dig even further when you have to deal with Hashes that also have Arrays within them.

## When Hash#dig is not enough?

In the previous example the addresses key contains a Hash, but this is often a soft guarantee. This means that when multiple addresses are present you may actually find an Array instead. For example:

```
client = {
  details: {
    first_name: "Florentino",
    last_name: "Perez"
  },
  addresses: [
    {
      type: "home",
      postcode: "SE1 9SG",
      street: "London Bridge St",
      number: 32,
      city: "London",
      location: {
        latitude: 51.504382,
        longitude: -0.086279
      }
    },
    {
      type: "office",
      postcode: "SW1A 1AA",
      street: "Buckingham Palace Road",
      number: nil,
      city: "London",
      location: {
        latitude: 51.5013673,
        longitude: -0.1440787
      }
    }
  ]
}

```

What's the problem here? Now not only addresses could be nil or not, but depending if the user has one address or multiple addresses the value of the :addresses key could be a Hash  or an Array . This is often the reality of many real-world hashes, and even though we could argue that the data structure design is wrong, somehow we have to deal with it.

## A simple solution

Let's assume that we want to collect all the latitude values of our client  addresses. Hash#dig will not work in this case simply because it doesn't know what to do as soon as an Array  is found:

```
puts client.dig(:addresses, :location, :latitude)
# `dig': no implicit conversion of Symbol into Integer (TypeError)
```

The code will have to fetch the :addresses  key. Then if it's a Hash use dig  to get the :latitude  from the location key. If it is an Array  it should iterate over all the addresses and collect the :latitude  from the various locations. Here it is:

```
def get_offices_latitudes_for(client)
  addresses = client[:addresses]
  return [] if addresses.nil?

  if addresses.is_a? Hash
    [ addresses.dig(:location, :latitude) ]
  else
    addresses.map { |address| address.dig(:location, :latitude) }
  end
end
```

And these are three simple tests that prove that it works:

```
client_with_no_addresses = {
  details: {
    first_name: "Florentino",
    last_name: "Perez"
  },
  addresses: nil
}

client_with_one_address = {
  details: {
    first_name: "Florentino",
    last_name: "Perez"
  },
  addresses:  {
    type: "home",
    postcode: "SE1 9SG",
    street: "London Bridge St",
    number: 32,
    city: "London",
    location: {
      latitude: 51.504382,
      longitude: -0.086279
    }
  }
}

client_with_many_addresses = {
  details: {
    first_name: "Florentino",
    last_name: "Perez"
  },
  addresses: [
    {
      type: "home",
      postcode: "SE1 9SG",
      street: "London Bridge St",
      number: 32,
      city: "London",
      location: {
        latitude: 51.504382,
        longitude: -0.086279
      }
    },
    {
      type: "office",
      postcode: "SW1A 1AA",
      street: "Buckingham Palace Road",
      number: nil,
      city: "London",
      location: {
        latitude: 51.5013673,
        longitude: -0.1440787
      }
    }
  ]
}

puts get_offices_latitudes_for(client_with_no_addresses).join(", ")
# empty string

puts get_offices_latitudes_for(client_with_one_address).join(", ")
# 51.504382

puts get_offices_latitudes_for(client_with_many_addresses).join(", ")
# 51.504382, 51.5013673

```

# Introducing Hash#dig\_and\_collect

I don't know about you, but I hate the previous code. How can we make it better? Being inspired by Hash#dig what we need here is a good default for navigating deeper our Hash  when we find an Array . I strongly feel a good solution is to _collect_ all the values, exactly like we did in our naïve solution.

Going back to our example, when a client does not have any addresse the code should return an empty array, _there was nothing to collect_.

```
client_with_no_addresses.dig_and_collect(:addresses, :location, :latitude)
# []

```

The scenarios in which a client has just one address ( addresses  key is a Hash ) or multiple addresses ( addresses  key is an Array ) should now be straightforward:

```
client_with_one_address.dig_and_collect(:addresses, :location, :latitude) 
# [51.504382] 

client_with_many_addresses.dig_and_collect(:addresses, :location, :latitude) 
# [51.504382, 51.5013673]
```

The implementation is fairly simple and you can read it on Github. We are monkey patching the Hash object, but I am sure it could be done better. Suggestions that involves Ruby refinements are more than welcome.

The solution recursively check what type of key you are trying to fetch and depending on the type recursively call dig\_and\_collect  either on a Hash  directly, or on all the elements in the Array  that you found along your path.

The rest of the code with the specs is available in this Github repo and I would really love to hear your feedback.

# Conclusion

In this blog I presented Hash#dig\_and\_collect , a simple utility method that is built on top of Hash#dig to help you navigate complex nested hashes. I found it really handy when dealing with badly designed Hashes out in the wild but I feel it could be helpful in other scenarios. Looking forward to hearing your thoughts.

If you enjoyed this blog post you can also follow me on twitter.

# References
