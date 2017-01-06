---
layout: post
title:  "Rails, RVM and project-specific configuration"
date:   2014-05-08 12:03
tags: rvm rails jekyll blog ruby
---

I've decided to try [Rails](http://rubyonrails.org). Finaly. =)

So, while I'm discovering Rails, I've got amazed by [rvm](https://rvm.io/).

Rvm
---

 * It's written on bash. I've not seen such huge bash script since winetricks. 
 * There is second version planned, written on ruby, and it [already has been funded](https://www.bountysource.com/teams/rvm/fundraiser).
 * It's quite agile and easy to use.
 * It supports [per-project ruby version and gemsets](https://rvm.io/workflow/projects), in it's own way (`.rvmrc`) or [in more portable way](https://rvm.io/workflow/projects#project-file-ruby-version), with `.ruby-version` and `.ruby-gemset`.
 
Actualy, I've got interested because of per-project settings. I'm already using [Jekyll](http://jekyllrb.com)
for this blog and I don't want to get any gem conflicts while trying rails, so,
I've created two separate gemsets - one for jekyll, and one for testing rails.
I like the .ruby-version approach more, so, I use it.

    ~/src/rails-blog-test $ rvm use 2.1
    ~/src/rails-blog-test $ rvm gemset create rails-test
    ~/src/rails-blog-test $ rvm --ruby-version use 2.1@rails-test
    ~/src/rails-blog-test $ bundle install
    ...
    ~/src/rails-blog-test $ cd ../ivan-kolmychek.github.io/
    ~/src/ivan-kolmychek.github.io $ rvm gemset create jekyll
    ~/src/ivan-kolmychek.github.io $ rvm --ruby-version use 2.1@jekyll
    ~/src/ivan-kolmychek.github.io $ gem install jekyll
    ...

And, after that, whenever I `cd` into any of that folders...

    ~ $ rvm gemset name
    /home/<username>/.rvm/gems/ruby-2.1.1
    ~ $ cd ~/src/rails-blog-test
    ~/src/rails-blog-test $ rvm gemset name
    rails-test
    ~/src/rails-blog-test $ cd ../ivan-kolmychek.github.io/
    ~/src/ivan-kolmychek.github.io $ rvm gemset name
    jekyll

I've got separated gem lists for each of that projects. That's just awesome. =)

Also, you can commit `.ruby-version` and `.ruby-gemset` files into your favorite
[DVCS](https://en.wikipedia.org/wiki/Distributed_version_control_system) and use
rvm in team and even while deploying your app to production servers.

Side note
---------

In ArchLinux, rvm complains about `--user-install` in `/etc/gemrc`.
I've just disabled it.

__Note__: do not comment whole line out, just remove option.

Before:

    gem: --user-install

After:

    gem:
