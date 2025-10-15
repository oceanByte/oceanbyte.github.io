---
layout: default
title: Latest Updates
---

{% assign sorted_changelogs = site.pages | where_exp: "page", "page.path contains 'changelog/'" | where_exp: "page", "page.date" | sort: "date" | reverse %}

<div class="homepage">
  <section class="latest-changelogs">
    <div class="list-intro">
      <div class="list-copy">
        <h1 class="page-title">Pontus-X updates</h1>
        {% if sorted_changelogs.size > 0 %}
        <p class="list-meta">Latest entry: {{ sorted_changelogs.first.date | date: "%B %d, %Y" }}</p>
        {% endif %}
      </div>
      {% if sorted_changelogs.size > 3 %}
      <a class="section-link" href="{{ '/archive/' | relative_url }}">View archive</a>
      {% endif %}
    </div>

    {% if sorted_changelogs.size == 0 %}
      <p class="empty-state">No changelogs yet&mdash;follow along for the next release.</p>
    {% else %}
      <div class="changelog-list">
        {% for changelog in sorted_changelogs limit:3 %}
        <article class="changelog-preview">
          <header>
            <h3><a href="{{ changelog.url | relative_url }}">{{ changelog.title }}</a></h3>
            <time datetime="{{ changelog.date | date_to_xmlschema }}">{{ changelog.date | date: "%b %d, %Y" }}</time>
            {% if changelog.sprint %}
            <p class="sprint-info">{{ changelog.sprint }}</p>
            {% endif %}
          </header>
          <div class="changelog-content">
            {{ changelog.content }}
          </div>
        </article>
        {% endfor %}
      </div>
    {% endif %}
  </section>

  <section class="resource-links">
    <div class="section-heading">
      <h2>Explore the ecosystem</h2>
    </div>
    <div class="resource-grid">
      <a class="resource-card" href="https://www.pontus-x.eu/" target="_blank" rel="noopener">
        <h3>Main Website</h3>
        <p>Learn about the vision and partners driving the Pontus-X open data economy.</p>
        <span class="resource-meta">pontus-x.eu →</span>
      </a>
      <a class="resource-card" href="https://portal.pontus-x.eu/#" target="_blank" rel="noopener">
        <h3>Pontus-X Portal</h3>
        <p>Discover datasets, services, and tooling available inside the Pontus-X portal.</p>
        <span class="resource-meta">portal.pontus-x.eu →</span>
      </a>
      <a class="resource-card" href="https://github.com/deltaDAO/" target="_blank" rel="noopener">
        <h3>GitHub Activity</h3>
        <p>Follow the engineering work across deltaDAO repositories powering the ecosystem.</p>
        <span class="resource-meta">github.com/deltaDAO →</span>
      </a>
    </div>
  </section>
</div>
