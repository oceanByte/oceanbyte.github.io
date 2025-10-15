---
layout: page
title: Changelog Archive
permalink: /archive/
---

<div class="archive">
  {% assign sorted_changelogs = site.pages | where_exp: "page", "page.path contains 'changelog/'" | where_exp: "page", "page.date" | sort: "date" | reverse %}

  {% if sorted_changelogs.size == 0 %}
    <p class="no-content">No changelogs available yet.</p>
  {% else %}
    <p class="archive-count">{{ sorted_changelogs.size }} changelog{% if sorted_changelogs.size != 1 %}s{% endif %}</p>

    {% for changelog in sorted_changelogs %}
      <article class="archive-entry">
        <time datetime="{{ changelog.date | date_to_xmlschema }}">{{ changelog.date | date: "%b %d, %Y" }}</time>
        <h3><a href="{{ changelog.url | relative_url }}">{{ changelog.title }}</a></h3>
        {% if changelog.sprint %}
        <p class="sprint-info">{{ changelog.sprint }}</p>
        {% endif %}
      </article>
    {% endfor %}
  {% endif %}
</div>
