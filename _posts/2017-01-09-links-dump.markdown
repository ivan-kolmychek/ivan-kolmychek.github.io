---
layout: post
title: 'Links: brevity in code, absurd observations and more'
date: 2017-01-09 19:00:00
tags: links code-style teaching software-engineering rsa ssl openssl linux opengl xkcd
---

Well, I've got a lot of good links, some new, some old. :)

This time it's a bunch of interesting questions about software engineering from
StackExchange, tool for making managing your little SSL CA much simpler, new
toy language you may find interesting and cool stories about state of graphical
drivers in Linux and OpenGL in general.

# [At what point is brevity no longer a virtue?][0]

While this question is asked about C#, the general thought expressed in accepted
(at the time of writing) answer can be interesting to a developer using any
language.

# [How should I respond to absurd observations from customers during software product demos?][1]

Both question and answers deal with miscommunication/misalignement of points of
views. I found them to be very interesting and enlightening.

# [How to deal with an intern's lack of basic skills?][2]

A question on Workplace@SO which title tells pretty much everything about the
question itself, but the accepted (at the time of writing) anwser

# [Simple RSA][3]

A good tool that comes in handy if you want/have to manage your own PKI, with
CA, creating and revoking certificates, etc. etc.

While, of course, for HTTPS server certificate you would probably be better
looking at some trusted CAs, if you want to set up client authentication using
certificates or VPN, this is an awesome tool to have. You can do most of these
things manually with OpenSSL, but the EasyRSA makes a lot of things related to
PKI management much easier.

# ["Installing certifiates onto android devices"][4]

Had to look it up when I tried to figure out how to install certificate for
client authentication to android device.

# [Charlie programming language][5]

A blog post on Crystal language site about developing a new toy language. Doesn't
have that much details, but still is pretty nice.

# A series of new and old articles from the Rich Geldreich about Linux, Games and OpenGL.

[End of year realization][6], [The Faster Zombies blog post][7],
[Things that drive me nuts about opengl][8] and
[The Trusth On OpenGL Driver Quality][9]

I've read them with great interest, as I try to follow the news about the state
of graphical drivers on Linux and the gaming there in general.

# [Emails by XKCD][10]

![Emails by XKCD][11]

[0]: https://softwareengineering.stackexchange.com/questions/339495/at-what-point-is-brevity-no-longer-a-virtue
[1]: https://workplace.stackexchange.com/questions/82435/how-should-i-respond-to-absurd-observations-from-customers-during-software-produ
[2]: https://workplace.stackexchange.com/questions/82346/how-to-deal-with-an-interns-lack-of-basic-skills
[3]: https://github.com/OpenVPN/easy-rsa
[4]: https://www.globalsign.com/en/blog/installing-certificates-onto-android-devices/
[5]: https://crystal-lang.org/2017/01/06/the-charly-programming-language.html
[6]: https://richg42.blogspot.com/2016/12/end-of-year-realization.html
[7]: https://richg42.blogspot.com/2017/01/the-faster-zombies-blog-post.html
[8]: https://richg42.blogspot.com/2014/05/things-that-drive-me-nuts-about-opengl.html
[9]: https://richg42.blogspot.com/2014/05/the-truth-on-opengl-driver-quality.html
[10]: https://xkcd.com/1783/
[11]: https://imgs.xkcd.com/comics/emails.png
