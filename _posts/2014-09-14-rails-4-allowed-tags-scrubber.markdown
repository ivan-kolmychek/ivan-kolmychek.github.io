---
layout: post
title:  "Rails 4 - better sanitizer with Loofah scrubbers"
date:   2014-09-14 01:24
tags: rails rails4 scrubbers sanitizer loofah nokogiri html
---

It's not a secret, that default `sanitize` helper method, shipped with Rails 4, is not so good.

For instance, it does not handle unclosed tags - so, if your user forget to close some `div`, your app layout may
be messed up a little bit. Or alot - it depends on your layout.

Also, it uses regex internally to parse HTML. It is a horrible way of getting that job done. [You definely don't want to do this](http://stackoverflow.com/a/1732454/2468200).

Fortunately, in Rails 5 [there will be cool new sanitizers](https://github.com/rails/rails-html-sanitizer), based on awesome [Loofah gem](https://github.com/flavorjones/loofah), which is based on famous [Nokogiri XML parser](http://nokogiri.org/) gem, which is based... You get the point - there is alot of very cool things to bring you enough power to clean up HTML. ;)

You can put it into your project right now, or you can add just Loofah and use custom scrubber instead - it's still nice to know, how to write them, because you may need to implement very uncommon scrubbing logic.

If you'll choose second option, [here is a gist](https://gist.github.com/ivan-kolmychek/ee2fdc53f3e2c637271d) with example of modified `:strip` built-in Loofah scrubber, which allows customizing the list of tags and attributes allowed. Usage tips included.

So, tame the Loofah scrubbers and you can ride <s>into the sunset</s> to the future of safe user-created HTML. ;)