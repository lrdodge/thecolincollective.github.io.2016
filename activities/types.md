---
layout: default
---
{% assign activities = site.activities | sort: "title" %}
{% assign groups = activities | group_by: "type" | sort: "name" %}

<div class="tags-expo">
  <div>
    {% for group in groups %}
    <a href="#{{ group.name | slugify }}" class="label label-primary">{{ group.name }}</a>
    {% endfor %}
  </div>
  <hr/>
  <div class="tags-expo-section">
    {% for group in groups %}
    <h2 id="{{ group.name | slugify }}">{{ group.name }}</h2>
    <ul class="tags-expo-posts">
      {% for activity in group.items %}

      <li>
        <a class="post-title" href="{{ site.baseurl }}{{ activity.url }}">
        {{ activity.title }}
        </a>
        <small>{{ activity.foci | join: ", " | downcase }}</small>
      </li>
      {% endfor %}
    </ul>
    {% endfor %}
  </div>
</div>
