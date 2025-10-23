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
        <div class="milestone-card-container status-{{ milestone.status | replace: ' ', '-' }}{% if milestone.currentProgress >= 100 %} is-complete{% endif %}">
          <div class="milestone-card-inner">
            <article class="milestone-card milestone-card-front">
              <header class="milestone-header">
                <h3>{{ milestone.title }}</h3>
                <div class="milestone-badges">
                  <span class="status-badge">{{ milestone.status }}</span>
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

            {% if milestone.successMetrics %}
            <article class="milestone-card milestone-card-back">
              <header class="milestone-header">
                <h3>{{ milestone.title }}</h3>
              </header>
              <div class="milestone-success-metrics">
                <h4>Success Metrics:</h4>
                <ul>
                  {% for metric in milestone.successMetrics %}
                  <li>{{ metric }}</li>
                  {% endfor %}
                </ul>
              </div>
            </article>
            {% endif %}
          </div>
        </div>
      {% endfor %}
    </div>
  {% endif %}
</div>
