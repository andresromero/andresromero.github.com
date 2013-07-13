---
layout: post
title: 
---
# <i class="icon-beaker icon-1x"></i> Research Interests
> Computer vision, image processing, machine learning, parallel architectures, embedded systems, GPU's,  object detection and tracking, color and texture image recognition.

## <i class="icon-keyboard icon-1x"></i> Programming Languagues
> C/C++,  Python, Java, Javascript, Perl, PHP, Postgresql, Shell Scripting, Sql.

## <i class="icon-desktop icon-1x"></i> Computer Architectures
> FPGA's, PIC's, DSP (TMS320C6400), ARM processors (Cortex A9).

# Recent post's
<div>
<ul id="posts">
  {% for post in site.posts %}
      {{ post.date | date: "%d %b %Y" }} <a href="{{ post.url }}">{{ post.title }}</a><br>
  {% endfor %}
</ul>
</div>
