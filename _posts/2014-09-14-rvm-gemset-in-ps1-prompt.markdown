---
layout: post
title:  "Display RVM gemset name in PS1 prompt"
date:   2014-09-14 02:06
tags: rvm gem ruby bash
---

Quick tip how to add `rvm` gemset name to PS1 prompt.

Put 

    rvm_ps1_indicator() 
    {
      command -v rvm-prompt >/dev/null 2>&1 && test -n "$(rvm-prompt g)" && printf "(%s) " "$(rvm-prompt)"
    }

    PS1='\[\033[01;36m\]\u\[\033[01;35m\]@\h\[\033[01;34m\] \w \e[01;31m\]$(rvm_ps1_indicator)\[\e[m\]\$\[\033[00m\] '
    
in `~/.bashrc` right after the loading `rvm`:

    [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*
    
Reload `~/.bashrc` file (or reopen a shell) and navigate to any directory with `.ruby-gemset` file inside - you should get gemset name displayed like on [this screenshot]({{ site.url }}/images/ssh-agent-confirmation.png)