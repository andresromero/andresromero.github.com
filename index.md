---
layout: masonry
title: Andrés Romero Mier y Terán
---
<hr>

##News
<div class="row">
	<div class="span12">
		<div id="myCarousel" class="carousel slide" style="margin: 0 auto">
		</div> 
	</div>
</div> 

<div class="row">
	<div class="span3">
		<img class="img-rounded" src="/static/images/andres3.jpg"/>
	</div>
	<div class="span9">		
		<h2 id="about-me">About me</h2>
		<p>I am a R&D Software Engineer in Computer Vision. I work on the design and evaluation of diferent image recognition algorithms at <a ref="www.planorama.com">The Planorama Group</a>. I got a PhD on Computer Vision and Architecture in 2013</p>

		<h2 id="i-classicon-beaker-icon-1xi-research-interests"><i class="icon-beaker icon-1x"></i> Research Interests</h2>
		<blockquote>
		  <p>Computer vision, image processing, machine learning, parallel architectures, embedded systems, GPU’s,  object detection and tracking, color and texture image recognition.</p>
		</blockquote>

		<h2 id="i-classicon-keyboard-icon-1xi-programming-languagues"><i class="icon-keyboard icon-1x"></i> Programming Languagues</h2>
		<blockquote>
		  <p>C/C++,  Python, Java, Javascript, Perl, PHP, Postgresql, Shell Scripting, Sql.</p>
		</blockquote>

		<h2 id="i-classicon-desktop-icon-1xi-computer-architectures"><i class="icon-desktop icon-1x"></i> Computer Architectures</h2>
		<blockquote>
		  <p>FPGA’s, PIC’s, DSP (TMS320C6400), ARM processors (Cortex A9).</p>
		</blockquote>
	</div>
</div> 

## Recent post's
<ul class="grid effect-2" id="grid">
  {% for post in site.posts %}
      <li>{{ post.date | date: "%d %b %Y" }} <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
