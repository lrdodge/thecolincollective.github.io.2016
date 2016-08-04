---
layout: minimal
title: What's New
subtitle: "#improvchickens"
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

    <p class="post-meta">
      Assimilated {{ activity.date | date: "%B %-d, %Y" }}
    </p>

    <div class="post-entry">
      {{ activity.content | strip_html | xml_escape | truncatewords: 50 }}
	  <a href="{{ activity.url | prepend: site.baseurl }}" class="post-read-more">[Read&nbsp;More]</a>
    </div>

   </article>
  {% endfor %}
</div>

{% if paginator.total_pages > 1 %}
<ul class="pager main-pager">
  {% if paginator.previous_page %}
  <li class="previous">
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&larr; Newer Posts</a>
  </li>
  {% endif %}
  {% if paginator.next_page %}
  <li class="next">
    <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Older Posts &rarr;</a>
  </li>
  {% endif %}
</ul>
{% endif %}
