---
title: Publishing on Quartz -- Simple & Effective
draft: false
tags:
  - quartz
  - hosting
time: 3 min
---
Squarespace, shopify, sellfy, and some’more; what do these have in common? Other than starting with an “S” they’re marketed as easy website/shop builders where you can publish a blog and do pretty much anything eCommerce. However, is the everything-in-one for over $30 a month really practical? Here on Medium we can share what’s on our mind, share links to products, and have a platform where others can find us easily, but someone wanting more freedom to experiment and host themselves (without worrying if a server will crash) will consider other options.

That’s what I’ve decided, after 5 years of experimenting with all the “S” sites, along with setting up my own website with pure code (elderwoodstea.com (experiment site, no purchases)), I also experimented with different note-taking apps like Notion, yet none stuck out to me as being the most flexible, akin to my mind, and creative as [Obsidian](https://obsidian.md/). Marketed as a “free and flexible app for your private thoughts”, this app is so much more than that. While Shopify builds everything for you, Obsidian allows you the freedom to build anything you want without the restrictions. Thanks to jzhao and his nifty tool, Quartz (lovin’ the igneous rock names), for $0 (except for $25 domain name with Cloudflare), I can build a website with a small framework that allows me to be my most creative and share what I need. How? By having direct access to code in an open-source Github repo clone.

### How does being a dev make this easier?

Often times being a “developer” gives people the vibe of a hard-core programmer who is obsessed with hard-to-learn coding concepts, yet in today’s day of open-source, this isn’t always the case.

While Shopify does everything for you with little-to-no access to code, Obsidian (and its framework, Quartz) gives full access to code thus making setting up a website affordable and more rewarding.

Sure, if you have a big business then it may be more affordable to get Shopify (depending on much it takes to hire your own dev), but for small projects like small eCommerce projects and hosting a blog, using a flexible solution makes the whole process easier, at least that I’ve observed.

## Steps in setting up Quartz

If you have Github the process is pretty simplified since Quartz has all the [steps on its website](https://quartz.jzhao.xyz/setting-up-your-GitHub-repository).

For a quick run-down of what I did, though, on my Arch Linux desktop. Firstly I:

1. Cloned the Quartz github repo (git clone [https://github.com/jackyzha0/quartz.git](https://github.com/jackyzha0/quartz.git) && cd quartz && npm i && npx quartz create).
2. Added Github repo on Github.
3. Signed in through command line (git remote set-url origin (add ssh key for repo in newly-made repo info here), ssh -T [git@github.com](mailto:git@github.com)) (This way I didn’t need to sign in with password).
4. Synced local github clone with github repo (npx quartz sync — no-pull).
5. When adding new changes, build code locally to see changes first (npx quartz build — serve) and then to add them to Github repo (npx quartz sync).

Now here’s how I hosted my Github repo on Cloudflare:

1. Go to Cloudflare Workers (automatic setup of deployment through their servers).
2. Add build command (npx quartz build).
3. Hit deploy button, and check for any errors (I had none after messing up the 1st time).
4. Go to settings in Cloudflare workers and add domain in Domains and Routes, enter your already-bought Cloudflare domain URL and website is connected!

Click around my website to see how it's worked out :D

I have a lot left to do for customization, updating all my Medium articles to it, and anything else I see fun to try. If you build your own Quartz digital garden, link it below and any questions you have. 

<h1 style="color: yellow">Happy writing!</h1>
