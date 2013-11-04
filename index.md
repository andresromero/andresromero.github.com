---
layout: masonry
title: Andrés Romero Mier y Terán
---
##News
<div class="row">
	<div class="span12">
		<div id="myCarousel" class="carousel slide" style="margin: 0 auto">
			<div class="carousel-inner">
				<div class="item active">
					<div class="hero-unit">
					    <h2>DASIP 2013</h2><em>Conference on Design and Architectures for Signal and Image Processing</em>, Oct 2013.
					    <h3>Real-time covariance tracking algorithm for embedded systems.</h3>
					    <h4>A.&nbsp;Romero Mier&nbsp;y Ter&aacute;n, L.&nbsp;Lacassagne, A.&nbsp;Hassan&nbsp;Zahraee, and
				  Gouiff&egrave;s.</h4>			    
					    <a href="dasip2013.pdf" class="btn btn-large btn-success">Read PDF</a>
					    <a href="slides/dasip2013_slides.pdf" class="btn btn-large btn-info">Slides</a>	
					    <a href="http://www.ecsi.org/dasip-2013" class="btn btn-large btn-default">DASIP 2013</a>
					</div>
				</div>
				<div class="item">
					<div class="hero-unit">
					    <h2>ICIP 2013</h2><em>IEEE, International Conference on Image Processing (ICIP)</em>.
					      IEEE, sep. 2013.
					    <h3>Total Bregman Divergence for Multiple Object Tracking.</h3>
					    <h4>A.&nbsp;Romero, M.&nbsp;Gouiff&egrave;s, and L.&nbsp;Lacassagne.</h4>			    
					    <a href="icip2013.pdf" class="btn btn-large btn-success">Read PDF</a>
					    <a href="http://www.icip13.org/" class="btn btn-large btn-default">ICIP 2013</a>	
					</div>
				</div>
				<div class="item">
					<div class="hero-unit">
					    <h2>Mirage 2013</h2><em>6th International Conference on Computer Vision / Computer Graphics Collaboration Techniques and Applications</em>.			      
					    <h3>Enhanced Local Binary Covariance Descriptor for texture analysis and object tracking</h3> 
					    <h4>A.&nbsp;Romero, M.&nbsp;Gouiff&egrave;s, and L.&nbsp;Lacassagne.</h4>	
					    <a href="mirage2013.pdf" class="btn btn-large btn-success">Read PDF</a>
					    <a href="slides/slides_mirage2013.pdf" class="btn btn-large btn-info">Slides</a>
					    <a href="http://mirage2013.hhi.fraunhofer.de/index.html" class="btn btn-large btn-default">Mirage 2013</a>
					</div>
				</div>
			</div>
			<a class="left carousel-control" href="#myCarousel" data-slide="prev">&lsaquo;</a>
			<a class="right carousel-control" href="#myCarousel" data-slide="next">&rsaquo;</a>
		</div> 
	</div>
</div>  

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
