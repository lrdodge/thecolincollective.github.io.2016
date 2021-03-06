---
layout: page
title: Group Mind
subtitle: The collective knowledge of the Collective.
css:
- /css/google-search-overrides.css
- /css/colin-activities.css
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

<div class="text-centered group-links">
  {% for focus in foci %}
  <a href="#{{ focus.name | slugify }}" class="btn btn-sml" role="button"><i class="fa fa-tag" aria-hidden="true"></i> {{ focus.name }}</a>
  {% endfor %}
</div>

<div class="text-centered">
  <ul class="list-inline">
    <li><i class="fa fa-user" aria-hidden="true"></i><i class="fa fa-user-plus" aria-hidden="true"></i> = people required</li>
    <li><i class="fa fa-clock-o" aria-hidden="true"></i> = one minute</li>
    <li><i class="fa fa-times" aria-hidden="true"></i><i class="fa fa-user" aria-hidden="true"></i> = per person</li>
    <li><i class="fa fa-times" aria-hidden="true"></i><i class="fa fa-users" aria-hidden="true"></i> = per scene</li>
    <li><a href="/activities" class="btn btn-info" role="button">Type</a></li>
  </ul>
</div>

<hr/>

{% for focus in foci %}
<h2 id="{{ focus.name | slugify }}"><u>{{ focus.name }}</u></h2>
<p>{{ focus.description }}</p>

{% for activity in activities %}
{% if activity.foci contains focus.name %}
<article class="post-preview">
  <a href="{{ activity.url | prepend: site.baseurl }}">
    <h3 class="group-heading">{{ activity.title }}</h3>
  </a>
  <div class="row">
    <div class="col-md-4">
      <span class="blog-tags">{{ activity.type }}</span>
    </div>
    <div class="col-md-3">
      {% for person in (2..activity.min-people) %}
      <i class="fa fa-user" aria-hidden="true"></i>
      {% endfor %}
      <i class="fa fa-user-plus" aria-hidden="true"></i>
    </div>
    <div class="col-md-3">
      {% for minute in (1..activity.duration)%}
      <i class="fa fa-clock-o" aria-hidden="true"></i>
      {% endfor %}
      {% case activity.duration-type %}
      {% when 'linear' %}
      <i class="fa fa-times" aria-hidden="true"></i><i class="fa fa-user" aria-hidden="true"></i>
      {% when 'step' %}
      <i class="fa fa-times" aria-hidden="true"></i><i class="fa fa-users" aria-hidden="true"></i>
      {% endcase %}
    </div>
  </div>

  <div class="post-entry">
    {{ activity.content | strip_html | xml_escape | truncatewords: 50 }}
    <a href="{{ activity.url | prepend: site.baseurl }}" class="post-read-more">[Read&nbsp;More]</a>
  </div>
</article>
{% endif %}
{% endfor %}
{% endfor %}
