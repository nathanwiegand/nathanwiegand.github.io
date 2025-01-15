---
layout: default
title: Links
permalink: /links/
---

# Links

{% for link in site.links %}
  <article class="link-entry">
    <h2><a href="{{ link.url | relative_url }}">{{ link.title }}</a></h2>
    {% if link.tags %}
      <div class="tags">
        Tags: {{ link.tags | join: ", " }}
      </div>
    {% endif %}
    {% if link.url %}
      <div class="external-link">
        <a href="{{ link.url }}" target="_blank" rel="noopener noreferrer">External Link</a>
      </div>
    {% endif %}
    {% if link.excerpt %}
      <div class="excerpt">
        {{ link.excerpt }}
      </div>
    {% endif %}
  </article>
{% endfor %}