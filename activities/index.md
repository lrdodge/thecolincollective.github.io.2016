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

{% assign activities = site.activities | sort: "title" %}

<div style="text-align: center;">
  <ul class="list-inline" style="display: inline;">
    <li><i class="fa fa-user" aria-hidden="true"></i><i class="fa fa-user-plus" aria-hidden="true"></i> = people required</li>
    <li><i class="fa fa-clock-o" aria-hidden="true"></i> = one minute</li>
    <li><i class="fa fa-times" aria-hidden="true"></i><i class="fa fa-user" aria-hidden="true"></i> = per person</li>
    <li><i class="fa fa-times" aria-hidden="true"></i><i class="fa fa-users" aria-hidden="true"></i> = per scene</li>
  </ul>
</div>
<hr/>
<div class="posts-list">
  {% for activity in activities %}
  <article class="post-preview">

    <a href="{{ activity.url | prepend: site.baseurl }}">
  	  <h2 class="post-title">{{ activity.title }}</h2>
    </a>

    <div class="row">
      <div class="col-md-2">
        <h3 class="post-subtitle" style="display: inline-block;">
          {{ activity.type }}
        </h3>
      </div>
        <div class="col-md-4">
        <span class="blog-tags">
          {% if site.link-tags %}
          {% for focus in activity.foci %}
          <a href="{{ site.baseurl }}/tag/{{ tag }}">{{ focus }}</a>
          {% endfor %}
          {% else %}
            {{ activity.foci | join: ", " | downcase }}
          {% endif %}
        </span>
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
</div>
