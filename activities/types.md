---
layout: default
---
{% assign activities = site.activities | sort: "title" %}
{% assign groups = activities | group_by: "type" | sort: "name" %}

<div>
  {% for group in groups %}
  <a href="#{{ group.name | slugify }}" class="label label-primary">{{ group.name }}</a>
  {% endfor %}
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
