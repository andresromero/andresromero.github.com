---
layout: masonry
title: Galería
carousel_images:
- /static/images/mieryteran1.jpg
- /static/images/mieryteran2.jpg
- /static/images/mieryteran3.jpg
- /static/images/herran2.jpg
- /static/images/mieryteran1.jpg
- /static/images/mieryteran2.jpg
- /static/images/mieryteran3.jpg
- /static/images/herran2.jpg
- /static/images/mieryteran1.jpg
- /static/images/mieryteran2.jpg
- /static/images/mieryteran3.jpg
- /static/images/herran2.jpg
- /static/images/mieryteran1.jpg
- /static/images/mieryteran2.jpg
- /static/images/mieryteran3.jpg
- /static/images/herran2.jpg
---

<ul class="grid effect-1" id="grid">
  {% for img in page.carousel_images %}
    <li><a href="{{img}}"><img src="{{img}}"></a></li>
   {% endfor %}
</ul>
