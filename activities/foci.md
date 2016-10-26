---
layout: page
title: Group Mind
subtitle: The collective knowledge of the Collective.
css: /css/google-search-overrides.css
---
{% assign foci = site.data.foci | sort: "name" %}
{% assign activities = site.activities | sort: "title" %}

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

<div style="text-align: center; padding-bottom: 10px;">
  {% for focus in foci %}
  <a href="#{{ focus.name | slugify }}" class="btn btn-default" role="button">{{ focus.name }}</a>
  {% endfor %}
</div>

{% for focus in foci %}
<h2 id="{{ focus.name | slugify }}">{{ focus.name }}</h2>
<p>{{ focus.description }}</p>
<ul>
{% for activity in activities %}
{% if activity.foci contains focus.name %}
<li><a href="{{ activity.url | prepend: site.baseurl }}">{{ activity.title }}</a></li>
{% endif %}
{% endfor %}
</ul>
{% endfor %}
