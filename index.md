---
layout: masonry
title: Andrés Romero Mier y Terán
---
<hr>
<div class="row">
	<div class="span3">
		<img class="img-rounded" src="/static/images/andres3.jpg"/>
	</div>
	<div class="span9">		
		<h2 id="about-me">About me</h2>
		<p>I am lecturer and researcher from the Parallel Systems team at the <a href="http://www.lri.fr">Laboratoire de Recherche en Informatique</a> from <a href="http://www.u-psud.fr">Paris Sud University XI</a>, where I work on the design, acceleration and implementation of computer vision algorithms.</p>

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
					    <a href="publications/dasip2013.pdf" class="btn btn-large btn-success">Read PDF</a>
					    <a href="publications/slides/dasip2013_slides.pdf" class="btn btn-large btn-info">Slides</a>	
					    <a href="http://www.ecsi.org/dasip-2013" class="btn btn-large btn-default">DASIP 2013</a>
					</div>
				</div>
				<div class="item">
					<div class="hero-unit">
					    <h2>ICIP 2013</h2><em>IEEE, International Conference on Image Processing (ICIP)</em>.
					      IEEE, sep. 2013.
					    <h3>Total Bregman Divergence for Multiple Object Tracking.</h3>
					    <h4>A.&nbsp;Romero, M.&nbsp;Gouiff&egrave;s, and L.&nbsp;Lacassagne.</h4>			    
					    <a href="publications/icip2013.pdf" class="btn btn-large btn-success">Read PDF</a>
					    <a href="http://www.icip13.org/" class="btn btn-large btn-default">ICIP 2013</a>	
					</div>
				</div>
				<div class="item">
					<div class="hero-unit">
					    <h2>Mirage 2013</h2><em>6th International Conference on Computer Vision / Computer Graphics Collaboration Techniques and Applications</em>.			      
					    <h3>Enhanced Local Binary Covariance Descriptor for texture analysis and object tracking</h3> 
					    <h4>A.&nbsp;Romero, M.&nbsp;Gouiff&egrave;s, and L.&nbsp;Lacassagne.</h4>	
					    <a href="publications/mirage2013.pdf" class="btn btn-large btn-success">Read PDF</a>
					    <a href="publications/slides/slides_mirage2013.pdf" class="btn btn-large btn-info">Slides</a>
					    <a href="http://mirage2013.hhi.fraunhofer.de/index.html" class="btn btn-large btn-default">Mirage 2013</a>
					</div>
				</div>
			</div>
			<a class="left carousel-control" href="#myCarousel" data-slide="prev">&lsaquo;</a>
			<a class="right carousel-control" href="#myCarousel" data-slide="next">&rsaquo;</a>
		</div> 
	</div>
</div> 



# Recent post's
<ul class="grid effect-2" id="grid">
  {% for post in site.posts %}
      <li>{{ post.date | date: "%d %b %Y" }} <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
