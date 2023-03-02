---
title: "Shell script example: Batch posting to Hugo"
date: 2023-01-29T22:23:17Z
draft: false
categories: [digital]
tags: [bash, hugo]
thumbnail:
---

While uploading my art to my website, I've found two use cases for shell scripts: editing the way I display images across all my posts, and converting a folder of images into posts all at once.

For those who don't know, the command line comes preinstalled with a bunch of tools to manipulate files. They are especially good for repetitive tasks like search and replace, sort, etc. When you write an executable file which uses the tools to complete some task, that's a shell script!  

It's fairly easy to find explanations of how to write shell scripts. This won't be a full tutorial. But it's hard to know what is possible at first, so I want to show some examples and point out which commands I'm using, if not exactly how.

In the following, I'm using Linux and the bash shell.

## Editing image codes across all posts

I write my posts in Markdown and originally added images to them using the default Markdown method, like this:

```
![Alt text for image](image.png)
```

This meant I couldn't fully customise how they were displayed because Hugo always renders them in a generic way. Eventually it became annoying. But by then I already had 50+ posts in my gallery. Time to use the command line.

I wanted to change each image to be displayed via this Hugo custom shortcode:

```
{{</* pic src="image.png" alt="Alt text for image" */>}}
```

So to start, I need a list of all the markdown files in my website, which I can get by going to the website folder and using the `find` command:

```
find . -type f -name '*.md' 
```

For each of those I'll need to do a search-and-replace. For this I use the `sed` command. Actually, let's try it on one file first by `cat`-ing it (printing it to the terminal) then piping it to `sed` with the `|` symbol.

```
username:~/catalogust$ cat content/gallery/dummy-post/index.md
---
title: "Dummy Post"
date: 2023-01-29T21:33:13Z
draft: false
tags: [untagged]
thumbnail:
---

![Alt text for image](image.png)
```

```
username:~/catalogust$ cat content/gallery/dummy-post/index.md | sed -r 's#!\[([^\[]*)\]\(([^)]*)\)#{{</* pic src="\1" alt="\2" */>}}#g'
---
title: "Dummy Post"
date: 2023-01-29T21:33:13Z
draft: false
tags: [untagged]
thumbnail:
---

{{</* pic src="Alt text for image" alt="image.png" */>}}
```

No, I'm not explaining that `sed` to you (laughs). Look up regular expressions and capture groups.

OK, so our two bits of finding files and editing text are working, how to put them together? Well, `find` has an option `-exec` which allows you to run a command on each file you found. (How are you meant to know it has that without reading the whole manual!? Look, I just found out about it from a StackOverflow answer.)

```
find . -type f -name '*.md' -exec sed -r 's#!\[([^\[]*)\]\(([^)]*)\)#{{</* pic src="\1" alt="\2" */>}}#g' {} \;
```

After running this, all the modified versions of my files get printed to the terminal. I scroll through them to see if anything turned out unexpectedly. (I actually had a few images with hyperlinks that got messed up. I fixed them manually, but if there were too many I could have written a script that replaced them separately.)

Now, to actually modify all the files, add the `-i` option to `sed` to make it modify files in place.

```
find . -type f -name '*.md' -exec sed -i -r 's#!\[([^\[]*)\]\(([^)]*)\)#{{</* pic src="\1" alt="\2" */>}}#g' {} \;
```

Nice! I didn't even have to make a script file, I did it all on the command line. I could still save it in a text file in case I want to do something similar in the future. But I can also see the command I used by running `history | grep pic` or something.

## Batch posting images

This one is more specific to making a gallery. I had a folder of images and I wanted to upload each one as a new page in Hugo with the following file structure:

```
artwork-name/
  index.md
  artwork name.png
```

index.md would need to have the correct front matter and display the image in the manner we saw in the previous section.

This time, I made an actual `gallerygen.sh` file and wrote the commands in there because I wanted to use shell variables. 

```
#!/bin/bash
IMAGES=$1
OUT=$2

for f in ./${IMAGES}*; do

file=$(echo ${f} | sed -r "s#.*/([^\^.]*\.*)#\1#")
name=$(echo ${file} | sed -r "s#([^.]*)\..*#\1#")
name_dashes=$(echo ${name} | sed -r "s# #-#g")

hugo new ${OUT}${name_dashes}/index.md

cp "${f}" "${OUT}${name_dashes}/${file}"

echo '{{</* pic src="'${file}'" alt="'${name}'" */>}}' >> ${OUT}${name_dashes}/index.md

done
```

At the top, after the "shebang" line, I read two arguments into variables, so when I run e.g. `./gallerygen.sh imagesfolder/ outputfolder/` I will be able to use those two paths. Then, you can see I used `find` to get the files again and `sed` to process each file path for use in different ways, storing the results in variables. I use `echo` a lot to print what I want to the command line so I can pipe it into further commands. I used Hugo's provided command `hugo new` to make my index.md pages, `cp` to copy the image files in, and `>>` to append the pic shortcode to each index.md file.  

Even if you have a nice `myscript.sh` file like this, there are two things to note when actually running it. Firstly, you have to call it via an absolute address (so if you are in the same folder with it, you have to call `./myscript.sh`, not just `myscript.sh`). Secondly, by default you can't run files! You have to use the `chmod` command to make it executable first.

Well... I didn't explain that very much! But I hope it gave you an idea of how different commands can be used together and what they can be used for. When in doubt, just search "how to do X command line" or "how to do X [command line tool]" and someone else has probably answered your question already.
