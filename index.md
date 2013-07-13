---
layout: post
title: 
---
#About me
Hi, I am a PhD student from [Paris Sud University XI](www.u-psud.fr), I work at the [Laboratoire de Recherche en Informatique](www.lri.fr) where I am developing on the design, acceleration and implementation of computer vision algorithms .

## <i class="icon-beaker icon-1x"></i> Research Interests
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
