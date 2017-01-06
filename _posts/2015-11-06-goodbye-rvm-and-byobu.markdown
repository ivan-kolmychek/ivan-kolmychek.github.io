---
layout: post
title: 'Goodbye, byobu and rvm. Hello, tmux and rbenv!'
date: 2015-11-06 13:11:00
tags: workspace byobu rvm tmux rbenv ruby
---

## tmux vs byobu

Byobu started to behave glitchy (again) after I had updated my system
yesterday - this is not the first time and I was not very satisfied with
it lately, - so, I looked up for a better way.

It turns out, that I didn't use most of the byobu's tuning anyway and
what I did could be easily replicated in the plain tmux config.

I was more surprised with first point - after all, byobu does it's tuning by the standard tmux features. I did not expect to get everything I need with really simple and minimalistic config file.

I guess that's because I chose byobu long time ago for it's widgets which were very useful for "text mode" work on the very low-performance (1 core, 0.7 GHz and 1.6 GHz later) when I did most of the stuff in the console with CLI utils, so, I really liked the status widgets it provided. It was useful for me for a long time; became an important part of my toolchain; survived a lot of software and hardware changes and, actually, made me to discover tmux at the first place. All this time I did not look into the byobu's internals, except for the migration from screen it used when I first adopted it, to tmux. It was glitchy, I understood that it's just a build over a screen (or tmux later), but it was just good enough.

You can find the current version of my tmux config in the [dotfiles][dotfiles] repo.

This whole situation reminds me of...

## rbenv vs rvm

The similar situation happened with RVM and rbenv.

When I'd re-discovered ruby for myself, I used RVM to install ruby and isolate projects dependencies using the built-in gemsets feature.

__Gemsets__ were ok for some time, but later I switched to Bundler and its `bundle exec`. Setting path bundle option to `vendor/bundle` helped to isolate the gems per-project. Bash aliases helped to not type "bundle exec" every time I wanted to launch tools like `rake`, `rspec`, `rails`, `sidekiq`, etc. etc.

But I still used RVM to install ruby - it was good enough in that role, until my colleagues pointed out to rbenv.

Its wiki has a [whole page][why-rbenv] explaining why rbenv is better, but I personaly like that it:

 * is really minimalistic; `rbenv` without plugins provides very basic functionality of switching the ruby versions;

 * does not pollute the shell - it loads very minimal hooks into shell, which, what is more important, are __optional__ - you can even not load it's hooks and use `rbenv exec` approach instead, which similar to `bundle exec` and is what I currently use.

 * has an intersting plugin system with some [pool of nice plugins][rbenv-plugins] already written - [ruby-build][rbenv-ruby-build], [default-gems][rbenv-default-gems],etc. etc.

So, again, it is small, focused, predictable, configurable and extendable, which makes it more maintainable. That's a very good reason to choose it as the tool for its job, regardless of how often I'm using it - it's nice with current use-almost-every-day scenario and I think it would still be ok for ocassinonal use if I will focus on some other language or technology else in future.

I want to have my tools maintainable, don't you? =)

[dotfiles]: https://github.com/ivan-kolmychek/dotfiles
[rbenv-plugins]: https://github.com/sstephenson/rbenv/wiki/Plugins
[rbenv-ruby-build]: https://github.com/sstephenson/ruby-build
[rbenv-default-gems]: https://github.com/sstephenson/rbenv-default-gems
[why-rbenv]: https://github.com/sstephenson/rbenv/wiki/Why-rbenv%3F
