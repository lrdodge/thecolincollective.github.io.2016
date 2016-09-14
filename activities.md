---
layout: page
title: Group Mind
subtitle: The collective knowledge of the Collective.
css: ../css/google-search-overrides.css
---
<script>
  (function() {
    var cx = '000078408709314139180:5grkwyhkvtc';
    var gcse = document.createElement('script');
    gcse.type = 'text/javascript';
    gcse.async = true;
    gcse.src = 'https://cse.google.com/cse.js?cx=' + cx;
    var s = document.getElementsByTagName('script')[0];
    s.parentNode.insertBefore(gcse, s);
  })();
</script>
<gcse:search></gcse:search>

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

    {% if activity.foci.size > 0 %}
    <div class="blog-tags">
      {% if site.link-tags %}
      {% for focus in activity.foci %}
      <a href="{{ site.baseurl }}/tag/{{ tag }}">{{ focus }}</a>
      {% endfor %}
      {% else %}
        {{ activity.foci | join: ", " }}
      {% endif %}
    </div>
    {% endif %}

   </article>
  {% endfor %}
</div>
