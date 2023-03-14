---
title: "Making a website, start to finish"
date: 2023-03-14T22:48:09Z
tags: [small web, self hosting]
draft: false
---

So, I have gone on about [why I made a website]({{< ref "/blog/personal-website-1" >}}). What's the actual process like for making a personal website then? Where to start?

## Planning

First, a website map. How do you want your pages to be organised? Maybe you want everything mixed together like in a traditional blog, maybe you would rather divide it up into sections. You will probably want an 'about' page. Visit other websites for inspiration.

{{< figure src="map.jpg" alt="map of a website with a homepage, links, gallery and writing section" caption="A quick sketch of my gallery website's current layout.">}}

Secondly, how do you want it to look? You could either browse existing themes for the website-maker you'll be using, or you could look up websites whose design you already enjoy and copy them. Keep in mind that a lot of people will visit your site via their phone, so you might want to make your site mobile responsive or even design it to look best on mobile.

There are also plenty of tools to help you design a website. An example I saw recently was this [retro, small-web-style one](https://sadgrl.online/projects/layout-builder/) (and despite being retro, this layout is mobile responsive!).

For my gallery website, I decided to make a mockup of how I wanted my website to look in a digital art program, referencing the look of another artist's website that I liked.

{{< figure src="mockup.jpeg" alt="sketchy digital mockup of an art website" caption="One of the mockup pages. Art is mine">}}

This was better than going in with no plan (which can lead to a lot of trial and error), but in hindsight I think just diving in with an existing theme and customising it - as I did for this blog - is best of all. I'm no web designer, and published themes have that extra touch of good taste that I can't achieve on my own.

## Preparation

After you build a whole website, it would be a shame to lose it, right? Set up a back-up system before you start.

My recommendation is to make a [Github](https://github.com/)[^1] account and learn to use the `git` tool to keep backups of your website there. 99% of the time you'll only need to know two commands (`git commit` and `git push`) so don't be scared! There is a reason everyone uses this tool - it's great at backing up project filess, and gives you the ability to undo things.

Isn't Git only for programmers to use though? No, it can be for any project! The only big way a website is different to a typical coding project is that it may have a lot of large image or audio/video files. However, this won't matter (especially not in the short term) - I've posted about this [here]({{< ref "/blog/ignoring-images" >}}).

[^1]: There are alternative sites hosting `git` repositories, like Gitea or sourcehut, which are not owned by Microsoft and maybe have other benefits, but I only have experience with Github. At least it's a mainstream option with a lot of support.

## Building

I wrote a post about different building tools [here]({{< ref "/blog/personal-website-2" >}}).

Now you've chosen your tools, next is the exciting and time-consuming part where your website plans become reality! Enjoy.

If you have lots of past content you want to upload, don't be daunted thinking about how long it will take. There are plenty of tricks you can use to automate such things. As a (rather technical) example, [here]({{< ref "/blog/batch-editing-and-posting" >}}) is how I bulk posted some art to my gallery site.

## Publish

I talked a little bit about it in my tools post, but right now the most established free hosting options for a personal website seem to be Neocities, Netlify, and Render. You'll probably also want to register a domain name (something like myname.com or example.net), but I would suggest leaving this for the final step - you typically can only buy a year's worth of use at a time, so you don't want to have a sudden change of heart.

As soon as you can open up the website on another device, congrats! You are now one of the happy few with a personal website.

But the story doesn't end here. Look forward to a future of linking it to successive people to show off your work, updating it with new stuff (and old stuff you forgot), reorganising, customising bits and bobs, and generally tinkering with it to your heart's content.

That, or leave it alone until the next time you need it. It won't disappear on you - it's your website, forever.
