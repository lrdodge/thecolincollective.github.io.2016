---
layout: page
title: Subsidiaries
subtitle: Patent Pending
---
<table>
  <tr>
    <th>Name</th>
    <th>Members</th>
  </tr>
{% for subsidiary in site.data.subsidiaries.subsidiaries %}
  <tr>
    <td>{{ subsidiary.name }}</td>
    <td>
      {% for member in subsidiary.members %}
        {{ member }}
      {% endfor %}
    </td>
  </tr>
{% endfor %}
</table>
