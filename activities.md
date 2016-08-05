---
layout: minimal
title: What's New
---

<div class="posts-list">
  {% for activity in site.activities %}
  <article class="post-preview">
    <a href="{{ activity.url | prepend: site.baseurl }}">
	  <h2 class="post-title">{{ activity.title }}</h2>

	  {% if activity.subtitle %}
	  <h3 class="post-subtitle">
	    {{ activity.subtitle }}
	  </h3>
	  {% endif %}
    </a>

    <div class="post-entry">
      {{ activity.content | strip_html | xml_escape | truncatewords: 50 }}
	  <a href="{{ activity.url | prepend: site.baseurl }}" class="post-read-more">[Read&nbsp;More]</a>
    </div>

   </article>
  {% endfor %}
</div>
