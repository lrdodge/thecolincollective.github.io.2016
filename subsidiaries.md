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
    <td>
      {% if subsidiary.name %}
        {{ subsidiary.name }}
      {% else %}
        <a href="mailto:thecolincollective@gmail.com?Body=Name:&Subject=Subsidiary%20Request%20for%20{{ subsidiary.members | url_encode }}" target="_blank">Submit</a>
      {% endif %}
    </td>
    <td>
      {% for member in subsidiary.members %}
        {{ member }}
      {% endfor %}
    </td>
  </tr>
{% endfor %}
</table>
