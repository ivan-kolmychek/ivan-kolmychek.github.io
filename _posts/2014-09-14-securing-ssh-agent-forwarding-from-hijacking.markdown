---
layout: post
title:  "Securing ssh-agent forwarding from hijacking"
date:   2014-09-14 00:54
tags: linux ssh ssh-agent ssh-forwarding security vagrant
---

I use [ssh-agent forwadring](https://developer.github.com/guides/using-ssh-agent-forwarding/) alot,
because it's a very convinient and simple way to securely use my ssh keys on remote hosts or inside [Vagrant](https://vagrantup.com) development.
It frees me from creating a bunch of keys - at least one for every host I use.

But forwarding is not secure by-default: [ssh-agent socket hijacking](http://www.clockwork.net/blog/2012/09/28/602/ssh_agent_hijacking) is possible by whoever
have `root` access to host you're forwarding your agent to.

Happily, there is no need to give up on such a useful instrument - that's why there isoption `-c` (from word `confirm`) in `ssh-add`.

Just add your key with such param:
    ssh-add -c ~/.ssh/my_cool_key.id_rsa
and there will be a confirmation window on every operation with an added key ([screenshot]({{ site.url }}/images/ssh-agent-confirmation.png)).

The app, used for confirmation window, usualy is the same, that for password requests (`ssh-askpass`, yep), but in this case there is no need for any password.
You can just click `OK` to accept operation or `Cancel` to decline it.

In case of declined operation, ssh-agent will not proceed with operation:

    ivanko@victoria ~/src/ivan-kolmychek.github.io (ruby-2.1.2@jekyll) $ git pull
    Agent admitted failure to sign using the key.
    Permission denied (publickey).
    fatal: Could not read from remote repository.

    Please make sure you have the correct access rights
    and the repository exists.
    ivanko@victoria ~/src/ivan-kolmychek.github.io (ruby-2.1.2@jekyll) $

For further details, see `man ssh-agent`.

Be safe out there. ;)

P.S. It is convinient to enforce this behavior as default. [Here is my question on SuperUser](http://superuser.com/questions/811392/ssh-agent-ssh-add-how-can-i-force-confirmation-by-default) about good ways to do so, besides adding a bash alias. If you know any, spare a few minutes to suggest it, please.

For people, who still interested in aliases - you can add

    alias ssh-add='ssh-add -c'

to your `~/.bashrc` file..
