---
layout: masonry
title: Masonry test
carousel_images:
  - /static/images/mieryteran1.jpg
  - /static/images/mieryteran2.jpg
  - /static/images/mieryteran3.jpg
  - /static/images/herran2.jpg
---

 <h1>Masonry - layout</h1>
  <p>Click to toggle item size</p>
  <div class="masonry">
   {% for img in page.carousel_images %}
    <img class="item" src="{{ img }}" />
   {% endfor %}
  </div>