---
layout: page
title: Pontus-X Milestones
permalink: /milestones/
---

<div class="milestones-page">
  <p class="intro">Track the overall goals and progress of Pontus-X development.</p>

  {% assign milestones_data = site.data.milestones.milestones %}

  {% if milestones_data.size == 0 %}
    <p class="no-content">Milestones coming soon!</p>
  {% else %}
    <div class="milestones-grid">
      {% for milestone in milestones_data %}
        <article class="milestone-card priority-{{ milestone.priority }}{% if milestone.currentProgress >= 100 %} is-complete{% endif %}">
          <header class="milestone-header">
            <h3>{{ milestone.title }}</h3>
            <div class="milestone-badges">
              <span class="priority-badge">{{ milestone.priority }}</span>
            </div>
          </header>

          <p class="milestone-description">{{ milestone.description }}</p>

          <div class="milestone-progress">
            <div class="progress-bar-container">
              <div class="progress-bar" style="width: {{ milestone.currentProgress }}%">
                <span class="progress-text">{{ milestone.currentProgress }}%</span>
              </div>
            </div>
          </div>

          <div class="milestone-meta">
            <p><strong>Target:</strong> {{ milestone.targetCompletion | date: "%b %Y" }}</p>
          </div>

        </article>
      {% endfor %}
    </div>
  {% endif %}
</div>
