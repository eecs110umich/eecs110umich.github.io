---
layout: default
title: Schedule
permalink: /schedule/
---

# Schedule

Here is what a typical week looks like. **Exact due dates and any changes always live on Canvas.**

{% comment %}
  Legend + Mon–Fri day cards render from site.data.course.weekly_calendar.
  Every event's `type` collapses to one of THREE calendar colors/categories:
    class | quiz | lab  → "Class"
    office_hours        → "Office hours"
    deadline            → "Deadline"
  The category name is printed under each pill (not just shown by color), so the
  meaning never depends on color alone.
{% endcomment %}

<ul class="cal-legend" aria-label="Calendar color key">
  <li><span class="pill-swatch pill--class" aria-hidden="true"></span> Class</li>
  <li><span class="pill-swatch pill--office_hours" aria-hidden="true"></span> Office hours</li>
  <li><span class="pill-swatch pill--deadline" aria-hidden="true"></span> Deadline</li>
</ul>

<ul class="cal-grid">
  {% for day in site.data.course.weekly_calendar %}
  <li class="card cal-day">
    <h2 class="cal-day__name">{{ day.day }}</h2>
    <ul class="cal-events">
      {% for event in day.events %}
      {%- assign cat = "class" -%}
      {%- assign cat_label = "Class" -%}
      {%- if event.type == "office_hours" -%}{%- assign cat = "office_hours" -%}{%- assign cat_label = "Office hours" -%}
      {%- elsif event.type == "deadline" -%}{%- assign cat = "deadline" -%}{%- assign cat_label = "Deadline" -%}{%- endif -%}
      <li class="cal-pill pill--{{ cat }}">
        {% if event.time and event.time != "" %}<span class="cal-pill__time">{{ event.time }}</span>{% endif %}
        <span class="cal-pill__label">{{ event.label }}</span>
        <span class="cal-pill__type">{{ cat_label }}</span>
      </li>
      {% endfor %}
    </ul>
  </li>
  {% endfor %}
</ul>

<p class="cal-note note">
  <strong>How each week connects:</strong> the in-class <strong>lab</strong> practices that day's
  lecture; the in-class <strong>quiz</strong> covers the previous week's lab; and the
  <strong>homework</strong> due that night covers the previous week's lecture.
</p>

<p class="cal-note note">
  Stop by office hours with questions and <strong>earn two engagement points each time.</strong>
  No appointment needed.
</p>
