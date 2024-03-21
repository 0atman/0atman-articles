---
title: The Iterate-and-Mutate Antipattern
layout: post
published_date: 2020-04-26 05:00:00 +0100
---

Names are powerful things. To name something is to control it. For years, I've been cautioning friends and colleagues about the following, which I consider a code smell:

```python

enabled_users = []
```
marginnote 'filter' "This code can be dramatically improved with many functional methods, in this case, a simple filter:<br/> `filter(users, is_user_enabled)` " %}
```python

for user in users:
    if user.enabled:
        enabled_users.append(user)
```



The part that makes me narrow my eyes, and the way you can identify this, is setting a variable to a null-y value, then opening up a for loop. I'll go into why I consider this bad practice in this article.

Until 3 days ago, I had no name for this pattern. Since Robb Shecter's [post](https://dogsnog.blog/2020/04/23/the-iterate-and-mutate-programming-anti-pattern/), I have one: _Iterate-and-mutate_.

## Every language is C (and other lies)

Programming languages aren't just ways to communicate instructions to machines, the are frameworks for thought.sidenote 'sapier' "In natural languages, this is called the [Sapir–Whorf hypothesis](https://en.wikipedia.org/wiki/Linguistic_relativity)" %} Every language (nearly) supports `if` statements and `for` loops, so it is easy to solve your programming problems with these constructs. However, it's NOT easy to read this code after it has been written.

We've all seen nested `if`s and `for`smarginfigure 'nested' "https://imgur.com/AMZYrnM.png" "You get the idea" %}, it's a famous way of writing spaghetti code. To understand the result of the `for` loop, the whole body must be inspected. Whoever looks at your code next must read many lines of code before they understand what is happening, because it can execute arbitrary, mutating, side-effecting code.

## Think about it

If you were to analyse the flow and swap out `if`s and `for`s with higher-level alternatives, they will more readable. Let's look at my toy example above: Switching the filtering `for` loop with the `filter` function, allows the reader a hint to what KIND of iteration we are doing.

```python
enabled_users = filter(users, is_user_enabled)
```

Immediately they can reason more about the code, they know that:

 - the new collection will have up to N itemssidenote 'nitems' "Where N is the size of the original collection, `users` in my example" %}
 - it will be a subset of the original collection
 - with some elements filtered out by some test codesidenote 'filterfn' "The well-named function `is_user_enabled`" %}

If we'd used a `for` loop, the reader would know that it's a `for` loop. Thanks, I hate it.

## Conclusion and Invocation

Once you are aware of the iterate-and-mutate pattern, you'll be able to think more critically at what kind of problems you're solving. Nearly all problems we face as programmers are iteration problems. `for`s don't help us much, we need to subcategorise. You'll start using not just functional methods more,sidenote 'fnmethods' "Such as `map`, `filter`, and list comprehensions" %} but the other high-level features of your language: Higher-order functions, closures, recursion, fluent interfaces, dependent types - OH MY!

In short, you might start enjoying again the great features that made you learn your language in the first place.
