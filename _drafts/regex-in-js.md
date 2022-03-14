---
title:  "Regex in Javascript"
date:   2022-03-03 07:00:00 -0800
categories: [javascript, regex]
author: Zynh Ludwig
---

I will preface this entire article with the fact that I am effectively taking the
information in the [MDN article](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/)
and presenting it in a slightly different format. Reading the MDN article is honestly
probably just as, if not more valuable than reading my own, this is largely for my own
comprehension.

That being said feel free to read mine anyway, I tried my best to scrape out superflous information,
or reorganize it in a way that is a bit more practical to use as a reference.

## What is Regex?

Regex, or Regular Expressions are patterns used to match character combinations
in strings. These patterns can be used in a variety of methods in `RegExp` and `String`

But a high level definition isn't helpful to anyone, so let's look at how we make a regular expression;

 - Regular Expression Literal:
{% highlight javascript %}
const re = /ab+c/; // Compiled at script load time.
                   // These perform the best, but can't be changed
{% endhighlight %}

 - You can also construct a `RegExp` object:
{% highlight javascript %}
const re = new RegExp('ab+c'); // These are compiled at runtime
                               // These perform a bit worse, but can be changed.
{% endhighlight %}

<br />

## Great Val, you still haven't told me anything...

Alright alright you caught me, I've been stalling.

This is because how regex is scary. So we know regex is used to find strings that meet certain conditions.
So lets start with the obvious question.

#### Why can't I just use indexOf()?

Let's create an example, if I have a string of text, and I only want to get instances of the string `"abc"`\\
I could rather easily just search for `"abc"` right?.

If the string I was parsing was `"Look the string I want: abc :How nice of it to be there"` it would give me exactly what I want.\\
But what about the string `"They took the slabcar out for a test drive."`...

Do we want to include the `"abc"` found in `"slabcar"`?\\
If so great! don't use regex! you'll thank me later.

But this isn't always the case, and it's just one example. What if my criteria are more flexible,
like I want any strings with an `"a"` followed by any number of `"b"`s, then ending in a `"c"`.

Not so easy to do with indexOf, huh?
