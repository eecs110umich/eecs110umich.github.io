---
layout: default
title: Staff
permalink: /staff/
---

# Staff

<ul class="staff-list">
  {% for member in site.data.course.staff %}
  {% comment %} Show a photo only if one is set and isn't the TODO placeholder;
     otherwise fall back to a neutral initial avatar so every card looks complete. {% endcomment %}
  {% assign has_photo = false %}
  {% if member.photo and member.photo != "" %}{% unless member.photo contains "todo" %}{% assign has_photo = true %}{% endunless %}{% endif %}
  {% assign first_name = member.name | split: " " | first %}
  <li class="card staff-card">

    <div class="staff-card__aside">
      {% if has_photo %}
        <img class="staff-photo" src="/{{ member.photo }}" alt="Photo of {{ member.name }}">
      {% else %}
        <span class="staff-photo staff-photo--placeholder" aria-hidden="true">{{ member.name | slice: 0 }}</span>
      {% endif %}

      <ul class="staff-meta">
        {% if member.pronouns and member.pronouns != "" %}<li>{{ member.pronouns }}</li>{% endif %}
        {% if member.email and member.email != "" %}<li><span aria-hidden="true">✉️</span> <a href="mailto:{{ member.email }}">{{ member.email }}</a></li>{% endif %}
        {% if member.hometown and member.hometown != "" %}<li><span aria-hidden="true">📍</span> {{ member.hometown }}</li>{% endif %}
      </ul>

      {% comment %} Emoji reveals: each is a focusable button whose descriptive
         text is exposed to screen readers (aria-label) AND shown visually on
         hover/focus (pure-CSS tooltip). Missing fields drop their emoji. {% endcomment %}
      <ul class="staff-reveals">
        {% if member.name_pronunciation and member.name_pronunciation != "" %}
        <li><button type="button" class="reveal" aria-label="Call me {{ first_name }} (pronounced {{ member.name_pronunciation | escape }})"><span class="reveal__icon" aria-hidden="true">🗣️</span><span class="reveal__tip" role="tooltip">Call me {{ first_name }} ({{ member.name_pronunciation }})</span></button></li>
        {% endif %}
        {% if member.class and member.class != "" %}
        <li><button type="button" class="reveal" aria-label="Class: {{ member.class | escape }}"><span class="reveal__icon" aria-hidden="true">🎓</span><span class="reveal__tip" role="tooltip">Class: {{ member.class }}</span></button></li>
        {% endif %}
        {% if member.major and member.major != "" %}
        <li><button type="button" class="reveal" aria-label="Major: {{ member.major | escape }}"><span class="reveal__icon" aria-hidden="true">📚</span><span class="reveal__tip" role="tooltip">Major: {{ member.major }}</span></button></li>
        {% endif %}
        {% if member.why_teach and member.why_teach != "" %}
        <li><button type="button" class="reveal" aria-label="Why I teach: {{ member.why_teach | escape }}"><span class="reveal__icon" aria-hidden="true">🍎</span><span class="reveal__tip" role="tooltip">Why I teach: {{ member.why_teach }}</span></button></li>
        {% endif %}
        {% if member.advice and member.advice != "" %}
        <li><button type="button" class="reveal" aria-label="Advice: {{ member.advice | escape }}"><span class="reveal__icon" aria-hidden="true">💡</span><span class="reveal__tip" role="tooltip">Advice: {{ member.advice }}</span></button></li>
        {% endif %}
        {% if member.ask_about and member.ask_about != "" %}
        <li><button type="button" class="reveal" aria-label="Ask me about: {{ member.ask_about | escape }}"><span class="reveal__icon" aria-hidden="true">❓</span><span class="reveal__tip" role="tooltip">Ask me about: {{ member.ask_about }}</span></button></li>
        {% endif %}
        {% if member.fun_fact and member.fun_fact != "" %}
        <li><button type="button" class="reveal" aria-label="Fun fact: {{ member.fun_fact | escape }}"><span class="reveal__icon" aria-hidden="true">🦈</span><span class="reveal__tip" role="tooltip">Fun fact: {{ member.fun_fact }}</span></button></li>
        {% endif %}
      </ul>
    </div>

    <div class="staff-card__main">
      <h2 class="staff-card__name">{{ member.name }}</h2>
      {% if member.role and member.role != "" %}<p class="role">{{ member.role }}</p>{% endif %}
      {% if member.blurb and member.blurb != "" %}<div class="blurb">{{ member.blurb | markdownify }}</div>{% endif %}
    </div>

  </li>
  {% endfor %}
</ul>
