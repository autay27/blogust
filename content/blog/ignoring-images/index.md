---
title: "To .gitignore or not to ignore"
date: 2023-02-12T23:50:06Z
draft: false
categories: [digital, web]
tags: [git, self hosting, hugo]
thumbnail:
---


If you're like me, you want to have gigabytes' worth of art hosted on your website, maybe videos too. And if you're like me, you want to back up your website with `git`, mainly because it's convenient. But also because it provides _versioning_ - a record of all the old versions of files, in case you want to go back to a previous version of the site.

Unfortunately, gigabytes' worth of updates will be slow to back up with `git`. Plus, versioning means that if you update your image files, the old versions are still hanging around taking up space. And if your website automatically generates some images - like thumbnails - these will get backed up even though they could just be generated again. All of these things will make your website's repository bigger and slower to back up.

> You can find many people online discussing whether to include images in a `git` project.
>
> There are solid arguments in favour of doing so - it's a good backup for those precious images, it's convenient, and storing your complete website means your hosting can automatically update your website every time you push to its repository.
>
> If you produce small image files, or rarely update your website, you're good. 

But let's suppose you don't want to store all your images in `git`, because after all, they don't need versioning. It would still be useful to back up text and code, and to be able to go back to a previous version if you mess up. What to do?

## Options

One solution would be to use an extension to `git` which is designed to handle large files such as images, such as `git-lfs` or `git-annex`. You can read a discussion of these [here](https://lwn.net/Articles/774125/). However, these require a little more care and in some cases compatible hosting. And they don't decrease the actual size of your project (I was a bit paranoid about not hitting Github's 10GB limit; this isn't a big concern).

Another hacky method is to store all your images in a different git repo which you include inside your website's repo as a _submodule_. If you push to this a lot less often, you'll avoid the slowness issue.

However, the simplest option is just a `.gitignore` file. You put it in your project's folder and it tells git not to back up certain things. For example, here is the gitignore file for this website at the time of writing:

```
# images that are not reused

content/**/*.png
content/**/*.gif
content/**/*.jpg
content/**/*.jpeg
content/**/*.webp

# hugo's generated resources i.e. more images

resources/**

# built version of site

public/*
```
`/**/` matches any number of directories, and `*` matches anything without a slash, i.e. any filename. `folder/**` matches anything inside `folder`. Anything that is matched will be ignored in commits. 

Don't forget to use the `git status` command to check that only the files you intended to ignore are not listed! Plus, if you already committed them once, they won't be automatically removed, you'll need to use `git rm --cached` (use that flag or you'll delete the file altogether).

You can back up all those images by other means - to start with, if they are digital artworks you probably have a backup in the form of your art program's save files. And once you publish your website, that's another backup. You can manually back up your website by putting it into a zip folder and uploading it somewhere or saving it on another device. And of course, there are ways to automate backups.
