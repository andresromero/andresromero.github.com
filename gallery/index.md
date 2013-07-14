---
layout: masonry
title: Masonry test
carousel_images:
  - /static/images/Tio Chuchis y Los 7 Hermanos.Jul 10,49 4 x 6.jpg
  - /static/images/Tio Chuchis con la familia Mier y Teraěn Julio 10,1949 4 x 6.jpg
  - /static/images/herran2.jpg
  - /static/images/winter.jpg
  - /static/images/Tio Chuchis y Los 7 Hermanos.Jul 10,49 4 x 6.jpg
  - /static/images/winter.jpg
  - /static/images/Tio Chuchis con la familia Mier y Teraěn Julio 10,1949 4 x 6.jpg
  - /static/images/herran2.jpg
  - /static/images/Tio Chuchis con la familia Mier y Teraěn Julio 10,1949 4 x 6.jpg
  - /static/images/herran2.jpg
  - /static/images/winter.jpg
  - /static/images/herran2.jpg
  - /static/images/winter.jpg
  - /static/images/Tio Chuchis y Los 7 Hermanos.Jul 10,49 4 x 6.jpg
  - /static/images/Tio Chuchis y Los 7 Hermanos.Jul 10,49 4 x 6.jpg
  - /static/images/Tio Chuchis con la familia Mier y Teraěn Julio 10,1949 4 x 6.jpg
---

<div id="container">
	{% for img in page.carousel_images %}
	<div class="masonryImage">
		<div class="image">
			<div class="trick"></div><a href="{{img}}"><img src="{{img}}"/></a>
		</div>
	</div>
	{% endfor %}
</div>