---
layout: default
title: Links
permalink: /links/
---
<style>
    .tag {
        color: darkorange;
    }
    .tags {
        display: flex;
        gap: 0.5rem;
        align-items: center;
    }
</style>

# Links

{% for link in site.links %}
  <article class="link-entry">
    <h2><a href="{{ link.url | relative_url }}">{{ link.title }}</a></h2>
    {% if link.external_url %}
      <div class="external-link">
        <a href="{{ link.external_url }}" target="_blank" rel="noopener noreferrer">{{ link.external_url }}</a>
      </div>
    {% endif %}
    {% if link.tags %}
      <div class="tags">
        Tags: 
        {% for tag in link.tags %}
          <span class="tag">{{ tag }}</span>
        {% endfor %}
      </div>
    {% endif %}

    {% if link.excerpt %}
      <div class="excerpt">
        {{ link.excerpt }}
      </div>
    {% endif %}
  </article>
{% endfor %}