---
layout: masonry
title: Andrés Romero Mier y Terán
---

## About me
I am a PhD student from the Architecture team of [Laboratoire de Recherche en Informatique](http://www.lri.fr) from [Paris Sud University XI](http://www.u-psud.fr), where I work on the design, acceleration and implementation of computer vision algorithms .

## <i class="icon-beaker icon-1x"></i> Research Interests
> Computer vision, image processing, machine learning, parallel architectures, embedded systems, GPU's,  object detection and tracking, color and texture image recognition.

## <i class="icon-keyboard icon-1x"></i> Programming Languagues
> C/C++,  Python, Java, Javascript, Perl, PHP, Postgresql, Shell Scripting, Sql.

## <i class="icon-desktop icon-1x"></i> Computer Architectures
> FPGA's, PIC's, DSP (TMS320C6400), ARM processors (Cortex A9).

# Recent post's
<ul class="grid effect-2" id="grid">
  {% for post in site.posts %}
      <li>{{ post.date | date: "%d %b %Y" }} <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
