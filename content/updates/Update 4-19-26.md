---
title: Update 4-19-26
draft: false
tags:
date: 2026-04-19
time: 2 min
---
> **Last updated**: [[Update 4-18-26]]

>**Wrote**: *(Updated)* [[What's a Digital Garden?]],  [[How to deal with Chiggers]]

## Site dev
*FINALLLLLYYYY* figured out how showing images works, for favicon anyway. The source input folder is in quartz/quartz/static whereas output *(where I kept copying images into)* is quartz/public/static. A different way of doing it than what I've seen before, because of the emitter plugin being used.

Also added the background image~ *WOOOOO IMMA SO HAPPYYY* 🎉
	*Reminder to myself where css styling page is:*

	cd quartz/quartz/styles && nvim base.scss

Now for the rest of images to show up on home page, I had to change src to static/(image name) instead of just the (image name).

Used Lunacy *(figma alt)* to edit images dimensions and put them in a single frame so they'd look right on site, worked out quite well.

The only problem is light mode is broken, might figure that out at some point... or not >;D