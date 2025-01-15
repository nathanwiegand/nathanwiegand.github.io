---
layout: default
title: Links
permalink: /links/
---

# Links

{% for link in site.links %}
  ## [{{ link.title }}]({{ link.url | relative_url }})
  {{ link.excerpt }}
{% endfor %} 