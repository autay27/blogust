---
title: "Walking around on Man Moel (and how to check focal length statistics)"
date: 2024-07-16T22:46:55+01:00
tags: [photography, wales]
draft: false 
---

Man Moel is a hill in South Wales. Nearby there is a tree farm and a wind farm.

{{< photofigure src="turbines.webp" caption="Wind farm" >}}
It's a quiet place that makes you realise how noisy the rest of the world is. But not too quiet, because there are sheep everywhere, and they like to talk to each other over long distances.

{{< photofigure src="sheep_hillside.webp" >}}
The sheep will look at you.

{{< photofigure src="sheep_above.webp" >}}
What if you head uphill? Well, apart from more sheep...


{{< photofigure src="sheep_path.webp" >}}
At the crest of the hill you will find a bench, which may have a man sitting photogenically in the middle of it.


{{< photofigure src="bench.webp" caption="I don't normally include strangers in my photos, but this was irresistible." >}}

There are long holes in the ground alongside the path.

{{< photofigure src="hole.webp" caption="This is an especially yonic one." >}}

And from the bench, there is a nice view of the nearby town Ebbw Vale.


{{< photofigure src="view_ebbwvale.webp" >}}

## other photography thoughts

My photos this time came out blurry and full of chromatic aberrations to the point where even I am bothered by it. Why? Probably because most of them were taken at 55mm, which is the most zoomed-in that my basic Canon kit lens can get (lenses do not tend to do well at their extremes). Why was I zooming in so much? Probably because everything I wanted to take pictures of was so far away from me. There is a different sense of scale in such a flat, open place. 

I already enjoy how detailed my DSLR photos are compared to the ones from my smartphone; at some point I should buy a better lens or two to sharpen them up further. Aside from lenses, I also want a better camera, so I could move away from Canon altogether if I wanted. I'm not sure what will push me to finally buy these things.

By the way, I use a handy command line tool called `exiftool` to check what focal length my photos were taken at. Here is an example for all my photos at Man Moel, showing the number of photos on the left and the focal length on the right:

```
~/Media/Canon450D/2024-07-14 man moel$ find [^\.]*.CR2 -exec exiftool -focallength {} + | grep Focal | sort | uniq -c
     11 Focal Length                    : 18.0 mm
      3 Focal Length                    : 25.0 mm
      2 Focal Length                    : 32.0 mm
      7 Focal Length                    : 35.0 mm
      1 Focal Length                    : 37.0 mm
      4 Focal Length                    : 41.0 mm
     10 Focal Length                    : 44.0 mm
      1 Focal Length                    : 46.0 mm
      1 Focal Length                    : 47.0 mm
      1 Focal Length                    : 48.0 mm
     50 Focal Length                    : 55.0 mm
```
