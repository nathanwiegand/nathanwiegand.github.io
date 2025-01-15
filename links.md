---
layout: default
title: Links
permalink: /links/
---

# Links

{% for link in site.links %}
## [{{ link.title }}]({{ link.url | relative_url }})
  {% if link.tags %}
    Tags: {{ link.tags | join: ", " }}
  {% endif %}
  {% if link.url %}
    [External Link]({{ link.url }})
  {% endif %}
  {% if link.excerpt %}
    {{ link.excerpt }}
  {% endif %}
{% endfor %} 
