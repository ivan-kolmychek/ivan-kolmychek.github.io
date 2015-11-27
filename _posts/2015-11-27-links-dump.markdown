---
layout: post
title: 'Links dump'
date: 2015-11-27 11:56:00
tags: links remote-working ascii screensaver redis javascript noscript ruby-object-mapper ruby rails progressive-enhancement everyone-has-js kafka event-sourcing clojure dynamic-languages static-languages
---

I've got a lot of interesting (for me) links piled up in the browser, so,
I've decided to post them here. 

Maybe you'll find something interesting for you too. ;)

## Disclaimer
I don't always agree with the content I'm linking to. 
It can have numerous flaws: it can be opinionated, obvious to someone, etc. etc. 
But I find it interesting and, maybe, thought-provoking.

# How Do Ruby/Rails Developers Keep Updated on Security Alerts?

A [short article][gavinmiller-security] about `bundler-audit`. 

# ASCII Screensaver

A [question on AskUbuntu][askubuntu-ascii-screensaver] about an ASCII screensaver.
Bunch of nice variants in the answers, including `cmatrix`.

# Redis data types

The [official documentation][redis-data-types] explains a lot about data types available in Redis.

# Ruby Object Mapper - first beta of 1.0.0

[ROM v. 1.0.0 [beta]][rom-1-0-0-beta] is now available, which is really nice because it means that ROM development team focuses more on the stabilization of the API for now. That's an importatnt thing to do, I guess.

# Understanding Transducers and The End Of Dynamic Languages

[Here][understanding-transducers] is a post by Elben Shira which dives into the
functional programming. Examples are in Clojure, but if you know JavaScript, you 
can get to understand them better by looking at 
[Clojure examples compared to JavaScript][clojure-compared-to-js]

There is another very interesting [post][the-end-of-dynamic-languages] with
a thought-provoking predictions about the fate of the dynamic languages and
how will the programming landscape turn to more strict languages in the
future.

I was kind of disappointed to find the religious reference
in the end of the post, but otherwise it's really nice.

# Effective Remote Working (+ Effective TDD With Ruby)

Here's also two nice posts by Luca Guidi - [Effective Remote Working][lucaguidi-effective-remote-working] and [Effective TDD With Ruby][lucaguidi-effective-tdd-with-ruby].

Both are opinionated but for me they offer an interesting insight, especialy his advices about things related to remote working stuff.

# Kafka for Ruby
Another [interesting post][kafka-for-ruby] about Kafka, Event Sourcing and Ruby.

# A little rant about "JAVASCRIPT! ENABLE IT NOW! DO IT"

One day I've got a post in the aggregator about using proc in the rails `asset_host` 
to be able to generate a different url for each asset. 

But when I open link to that article in my browser with JavaScript turned off 
(I use `NoScript` in whitelisting mode) I get the "loader" anmation.

What's weird is that I can see the content for a second before the "loading" 
animation appears. Looking at the DOM shows that content is really loaded - you 
can simply remove the loading element and read all of it without any trouble.

So, the question is: why would they cover up their __already loaded__ content which 
__does not require JavaScript__ with that nasty loader?

[Everyone has the JavaScript, right?][everyone-has-js]

Please, don't do that. 
Consider [Progressive Enhancement][progressive-enhancement] instead.

BTW, [here][cookieshq-demands-the-javascript] is a link to the article if you want 
to see what I'm talking about.

# That's all

Wow, that pile is less that I've though it is. 
Ok, now I can begin to raise a new one. :)

[gavinmiller-security]: http://gavinmiller.io/2015/staying-up-to-date-with-security-alerts/
[askubuntu-ascii-screensaver]: http://askubuntu.com/questions/699579/ascii-screensaver-for-the-command-line-or-a-tui
[redis-data-types]: http://redis.io/topics/data-types
[rom-1-0-0-beta]: http://rom-rb.org/blog/2015/11/24/first-beta-of-rom-1-0-0-has-been-released/
[lucaguidi-effective-remote-working]: http://lucaguidi.com/2015/10/13/effective-remote-working.html
[lucaguidi-effective-tdd-with-ruby]: http://lucaguidi.com/2015/10/20/effective-tdd-with-ruby-time-and-flow.html
[cookieshq-demands-the-javascript]: http://cookieshq.co.uk/posts/rails-tips-asset-host-proc/
[everyone-has-js]: http://kryogenix.org/code/browser/everyonehasjs.html
[progressitve-enhancement]: https://jakearchibald.com/2013/progressive-enhancement-still-important/
[kafka-for-ruby]: http://teamcoding.com/blog/2015/10/05/kafka/
[understanding-transducers]: http://elbenshira.com/blog/understanding-transducers/
[the-end-of-dynamic-languages]: http://elbenshira.com/blog/the-end-of-dynamic-languages/
[clojure-compared-to-js]: http://elbenshira.com/p/clojure-primer-js/
