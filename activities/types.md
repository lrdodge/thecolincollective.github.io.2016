---
layout: page
title: Group Mind
subtitle: The collective knowledge of the Collective.
css: /css/google-search-overrides.css
---
{% assign activities = site.activities | sort: "title" %}
{% assign groups = activities | group_by: "type" | sort: "name" %}

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
  {% for group in groups %}
  <a href="#{{ group.name | slugify }}" class="btn btn-default" role="button">{{ group.name }}s</a>
  {% endfor %}
</div>

<div style="text-align: center;">
  <ul class="list-inline" style="display: inline;">
    <li><i class="fa fa-user" aria-hidden="true"></i><i class="fa fa-user-plus" aria-hidden="true"></i> = people required</li>
    <li><i class="fa fa-clock-o" aria-hidden="true"></i> = one minute</li>
    <li><i class="fa fa-times" aria-hidden="true"></i><i class="fa fa-user" aria-hidden="true"></i> = per person</li>
    <li><i class="fa fa-times" aria-hidden="true"></i><i class="fa fa-users" aria-hidden="true"></i> = per scene</li>
  </ul>
</div>

<hr/>

{% for group in groups %}
<h2 id="{{ group.name | slugify }}">{{ group.name }}s</h2>

{% for activity in group.items %}
<article class="post-preview">
  <a href="{{ activity.url | prepend: site.baseurl }}">
    <h3 style="display: inline-block; margin-top: 0;">{{ activity.title }}</h3>
  </a>

  <div class="row">
    <div class="col-md-4">
      <span class="blog-tags">{{ activity.foci | join: ", " | downcase }}</span>
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
{% endfor %}

{% endfor %}
