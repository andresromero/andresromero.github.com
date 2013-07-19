---
layout: post
title: Tiling a large collection of images automatically
---

For my thesis manuscript I needed to create a mosaic of images showing the evolution of the taget's appearance in time. So I found this extremely useful line of code from ImageMagick:

{% highlight bash %}
montage frame*.ppm -tile 30x30 -geometry +1+1 mosaic_%d.ppm
{% endhighlight %}

where `frame*.ppm` are output images from my tracking algorithm and `mosaic_%d.ppm` is the pattern of the mosaics: it can create many images depending on the tiling parameters and the number of frames.

The results obtained are something like this:

![alt text][panda]

[panda]: /static/images/pandaSeq.jpg "Panda sequence"
