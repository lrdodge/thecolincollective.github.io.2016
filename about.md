---
layout: page
title: About
subtitle: Not a Cult
permalink: /about/
comments: false
author_footer: false
bigimg:
- "/img/skyline-min.jpg"
---
Experimenters and dabblers: The Colin Collective taps unusual inspiration and explores new realms. Born across the globe, eight diverse and unique individuals were summoned together by pheromones and mystical forces to become Colin. We excel in experimenting with original formats and dare to play big. Based out of Kansas City, The Colin Collective has been performing long form improvisation and being generally silly since 2015.

Members of The Colin Collective have a wide spectrum of backgrounds, from acting to computer science to juggling to transportation logistics. Most are involved in additional improv groups, including Comedy City, Kansas City Improv Company, Babies, and That’s No Movie. The Colin Collective can be seen regularly at the Kick Comedy theater and has made appearances at the 2016 Kansas City Improv Festival and the 2016 Denver Improv Festival.

<div id="carousel-example-generic" class="carousel slide" data-ride="carousel">
  <div class="carousel-inner" role="listbox">
    {% for photo in site.data.photos %}
    {% if forloop.first %}
    <div class="item active">
    {% else %}
    <div class="item">
    {% endif %}
      <img src="{{ site.baseurl }}{{ photo.path }}" alt="{{ photo.alt }}">
      <div class="carousel-caption">
        {{ photo.caption }}
      </div>
    </div>
    {% endfor %}
  </div>
  <a class="left carousel-control" href="#carousel-example-generic" role="button" data-slide="prev">
    <span class="icon-prev" aria-hidden="true"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="right carousel-control" href="#carousel-example-generic" role="button" data-slide="next">
    <span class="icon-next" aria-hidden="true"></span>
    <span class="sr-only">Next</span>
  </a>
</div>
