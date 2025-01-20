# Nathan Wiegand

<h2>Recent Links</h2>
<ul>
  {% for link in site.links limit:5 %}
    <li>
      <a href="{{ link.url }}">{{ link.title }}</a>
      {% if link.external_url %}
        - <a href="{{ link.external_url }}" target="_blank" rel="noopener noreferrer">[external link]</a>
      {% endif %}
    </li>
  {% endfor %}
</ul>

{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.date | date: "%B %Y" }} - {{ post.title }}</a></li>
    {% endfor %}
  </ul>
  <ul>
	  {% for blog in site.pages %}
	    <li>
	      <a href="{{ blog.url }}">{{ blog.title }}</a>
	    </li>
	  {% endfor %}
  </ul>

{% endfor %}
