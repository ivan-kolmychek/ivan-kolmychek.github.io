---
layout: post
title: "Links: you don't deprecate enough and more"
date: 2017-01-08 13:00:00
tags: links ruby rails brainfuck tdd deprecations background-jobs hashie
---

Wow, it's been a while since I've shared links, and I have a big pile of
them now. Maybe, sharing them a bunch per post would be at least readable.

This time it's about BrainFuck interpreter in Ruby, some new stuff from ruby 2.4,
discussion of deprecations and hashie and suggestions how to improve background
jobs performance in Rails.

# [BrainFuck interpreter written in Ruby with TDD.](https://github.com/yukas/brainfuck)

Specs are written in MiniTest.

I would really prefer RSpec (or at least Spec falvor of MiniTest) but it's
still interesting.

# [Compare-by-identity in Set in Ruby 2.4](https://blog.bigbinary.com/2016/12/29/ruby-2-4-adds-compare-by-identity-functionality-for-sets.html) and [UUID as type of PK column in Rails 5](https://blog.bigbinary.com/2016/04/04/rails-5-provides-application-config-to-use-UUID-as-primary-key.html)

These are ones of many "hey, here's a heads up on what new to expect in the new
Ruby/Rails version" from awesome guys at BigBinary. By the way, they don't only
write good and concise articles about new stuff, but also react to feedback very
quickly, in my experience. :)

The second one is a bit old but still is useful and that's what I found when I
had to look up for a reminder how to do it.

# [The Straight Dope On Deprecations](https://blog.codeship.com/the-straight-dope-on-deprecations/)
A very nice, in-detail take on deprecations, with examples on how to do them
the right way and
a very interesting thought throughout the post - "you're not deprecating enough".

It also links to ["Hashie considered harmful"](https://www.schneems.com/2014/12/15/hashie-considered-harmful.html)
which, whiles published in the end of 2014, still is a very good post.
It explains why you probably don't need Hashie and what to use instead.

# [Ruby Standard Library](https://www.blackbytes.info/2016/05/ruby-standard-library/)

Short recap on some of the things that Ruby standard library can do that you
might not knew it can.
Not much new for me personally there, to be honest, but it's still a pretty
good reminder.
You may find something new for yourself.

The author behind BlackBytes, Jesus Castello, also reacts to the feedback very
quickly.

# [Improving Rails Performance with Better Background Jobs](https://blog.codeminer42.com/improving-rails-scalability-with-better-architecture-c102a2a0cdec)

Pretty big and detailed article describing step by step some of ways to
optimize the background jobs.

# [Team Chat - XKCD](https://xkcd.com/1782/)

![Team Chat by XKCD](https://imgs.xkcd.com/comics/team_chat.png)
