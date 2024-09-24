---
title: "Tools for building websites"
date: 2023-01-22T21:32:34Z
draft: true
categories: [web]
tags: [small web, self hosting]
thumbnail: example_content.png
---

Last time I talked about [why I made a personal website]( {{< relref "blog/personal-website-1" >}} ). But what tools did I use to do it? Well, actually, I've made a personal website three times now, so a few different ones. 

I started off with a wiki, which was clunky and couldn't adapt to my needs, but I'm now using an SSG which allows me to extend my website however I like. Plus I've struggled a lot finding hosting that's free/cheap and suitable for a hobbyist. Let's learn from my mistakes!

> This is a braindump of my experiences with various tools, not a comprehensive resource. I wanted to write for people with little prior experience, who might not know the terminology commonly used to talk about these things.

## A wiki with just one user?

When I started out, I just wanted to store information about my original characters and universes, so I decided to make a wiki. 

Specifically, I used the application DokuWiki.

{{< figure src="catalogust_dokuwiki.png" alt="A character profile on a wiki entitled 'catalogust'" caption="The result of my efforts with DokuWiki" >}}

Pros of wiki applications: 
- Works (almost) out of the box.
- Can be edited from the browser.
- Automatic edit history/easy rollbacks for each page.
- Can use community plugins for things such as image galleries and slideshows.
- Could be used to collaborate with friends, since anyone with an account can edit.

Cons of wiki applications:
- Must be edited from the browser unless you understand the how the data is organised within the application. The browser editor can be annoying to use.
- Depending on which wiki application you use, it may require working with a database. DokuWiki does not.
- Not static (requires a server that can run PHP or something). This also poses more of a security risk for the website.
- Difficult to customise the workings or appearance of the website.
- Annoying to upload and manage images.

Honestly, I think a wiki is only worth it if you have multiple users collaborating in real time. That is what wikis are designed for, they are great for it, and they are a hassle for anything else.

## A website I can post on

After I realised I wanted a general gallery without the hassle of the wiki, I actually made a website by hand with HTML and CSS. 

{{< figure src="catalogust_html.png" alt="A greenish website displaying titles and thumbnails for art, categorised by year and subject" caption="You can tell I discovered flexboxes and got a bit too excited" >}}

I had a vague idea that I could write a program which would generate the HTML for me, if given the writing and images for each page, but I thought I would do it later...

Then I found out that static site generators (SSGs) already exist! They are a simple way to generate a full website from content files (i.e. your text and images), with automatic pagination and other stuff that you would expect to find on a blog, gallery or social media page. You can add metadata to your content, such as tags or summaries. Essentially, it allows you to *post*. I was sold immediately. 

I am now using the SSG Hugo. A popular option is Github Pages + Jekyll. There are plenty of others.

{{< figure src="example_content.png" alt="A screenshot of the text editor VSCode. On the left, the file structure of this website is open, with the folder for this blog post open to reveal a text file and the images used in the post. On the right, the start of this blog post is displayed, with metadata above it including a title, tags, and the date of posting." caption="On the left is part of the structure for this blog, including the folder for this post. On the right is the text file used to generate this post." >}}

Pros of SSGs:
- Fairly easy to get started, large user base with lots of tutorials.
- Static (don't need to host it on a server running PHP or SQL).
- Make posts and edit with whatever text editor you like.
- Preview the website offline.
- Easy to understand the file structure as it usually corresponds 1:1 with the resulting website.
- Many themes available to customise your site (or you can make your own).
- Provides ways for you to re-use content between pages.
- You can switch to a different SSG and re-use the same content files.
- Back up your content without backing up the whole website.

Cons of SSGs:
- No automatic edit history/versioning, although this is easy to achieve via the popular tool `git`.
- Need to edit from your device and publish edits to the hosting service.
- Need to learn about some new concepts like frontmatter, templates, the command line, etc. in order to use it to its full potential.

I see an SSG as a good step up from a blogging platform like WordPress or Tumblr. I really like that my website boils down to a bunch of text files saved on my computer. Plus, the fact it's static means that I can easily find free hosting. It's true that it requires a little more time to get to grips with, but I think the learning experience is intuitive and fun.

## Hosting 

I've tried three different hosting providers so far. I only used their basic features but at least I can give my perspective as a hobbyist.

> There are countless hosting providers out there, especially for static content. A notable one is [Neocities](https://neocities.org/), which is free, intended for personal websites and has a social-network aspect to allow you to meet other 'small web' creators.

### Render and Netlify

These are two different providers I've used, both of which allow you to host static sites for free. Netlify is much more popular and established.

- Render
  - Must upload via git repo (e.g. Github); simple integration with an SSG
- Netlify
  - Able to upload via git repo and integrate with an SSG but can also upload directly
  - When I tried to upload via their CLI interface on Linux, it was broken and not easily fixable; I had to use their website.

Since I don't want to store all of the image files for my website in a git repo (they don't require versioning!), I currently prefer Netlify since it allows me to upload my website directly. It is a hassle to have to do it via their website though.

### NearlyFreeSpeech.NET
- Able to run a server, things like PHP, SQL, etc.
  - Pay as you go; if you have to host a large number of images it may become expensive
  - Free and active user forum where you can request support (professional support is paid)

NFS advertises itself as not for beginners. But what does that mean really? I decided to jump in and use it for my wiki because I wanted the PAYG model. My starter knowledge was only how to use Linux via the command line. And this turned out fine! The wiki worked pretty much out of the box. You won't get professional support unless you pay extra, but the free community forum has a member of staff on hand who is quick to reply with help.

However, the next time I used their hosting was when I wanted to host a comment server for my blog. As soon as I wanted to do something involving _installing software and running background processes_, being a beginner felt like a problem. NFSN grants you certain permissions only through their web interface. Their machines also run a custom OS. This means that the majority of tutorials online, aimed at people setting up a server on a PC running Ubuntu or what not, don't exactly apply. I think this makes things harder for a beginner than they need to be.

> I eventually gave up on hosting my comment server on NFSN when I started experiencing a bug on their OS and read that they don't plan to fix it. I'll try again on different hosting in the future.

## Conclusion 

It can be hard to find information about building and hosting a website just by Googling. A lot of stuff is aimed at people running businesses who need to support hundreds of thousands of visitors with 100% uptime or some such. I hope that this post could be helpful to hobbyists.

Keep in mind I only talked about the things I've actually used. There are countless web hosting providers out there, and plenty of alternative website building tools - I'll list some that I've heard of recently:

- Wordpress (blogging/CMS)
- Ghost (blogging/CMS)
- WriteFreely (blogging)
- Piwigo (gallery site)

There are plenty more if you dig around. Warning: the top results on Google are full of website making *services* such as Wix, Squarespace and so on (the CMS options above also offer such services). But services don't let you own your website - you're tied to them for everything. That defeats the point if you ask me.

Next time I'll talk about the actual process of creating my (latest) website, from the planning stage to creation and the challenges of uploading a large amount of past artworks.
