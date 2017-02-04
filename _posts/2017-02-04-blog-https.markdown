---
layout: post
title: 'HTTPS for site on GitHub Pages with custom domain'
date: 2017-02-04 11:30:00
tags: blog https github-pages custom-domain cloudflare
---

I've been using github.io subdomain for a blog for some time.
That's because if you attach custom domain to GitHub Pages site
then trying to visit it over HTTPS will produce an error.

That's because GitHub Pages use certificate issued for `*.github.io`,
and not for your custom domain, which is pretty logical.

So, how can you combine GitHub Pages, custom domain and still get
working HTTPS?

# CloudFlare to the rescue!

You can sign up for the free CloudFlare plan, put your custom domain
through it and let the CloudFlare terminate the SSL.

For this you need:

 * [Setup custom domain on GitHub Pages][github-custom-domain]

 * Plug it into the CloudFlare and set up HTTPS

 * (Optionally) [Add page rule to redirect HTTP trafic to HTTPS.][redirect-https]

 * Test that everything working :)

And you're set up.

So, as you probably already noticed, I've tested this myself so far and now
this blog is available as `https://ivan.kolmychek.name`.

[github-custom-domain]: https://help.github.com/articles/using-a-custom-domain-with-github-pages/
[redirect-https]: https://support.cloudflare.com/hc/en-us/articles/200170536-How-do-I-redirect-all-visitors-to-HTTPS-SSL-
