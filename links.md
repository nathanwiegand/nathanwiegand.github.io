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
    .external-link {
        color: darkorange;
        font-size: 0.8em;
    }
    article {
        margin-bottom: 1rem;
    }
</style>

# Links

{% for link in site.links %}
  <article class="link-entry">
    <a href="{{ link.url | relative_url }}">{{ link.title }}</a><br>
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