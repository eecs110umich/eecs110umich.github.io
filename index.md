---
layout: default
# No page.title on the home page, so the browser tab shows just the course name.
---

{%- assign course = site.data.course.course -%}
{%- assign meeting = site.data.course.meeting -%}

<div class="banner">
  <!-- TODO: replace banner (assets/img/banner.jpg is a placeholder). -->
  <img src="/assets/img/banner.jpg" alt="Abstract computer-science banner">
</div>

<header class="page-header">
  <h1>{{ course.code }}: {{ course.name }}</h1>
  {% if course.tagline and course.tagline != "" %}<p class="tagline">{{ course.tagline }}</p>{% endif %}
  <p class="course-meta">
    <span>{{ course.term }}</span>
    <span>{{ course.credits }} credits</span>
    <span>{{ course.university }}</span>
    <span>Meets {{ meeting.day }}s, {{ meeting.time }} &middot; {{ meeting.location }}</span>
  </p>
</header>

<p class="lead">
  {{ course.code }}: {{ course.name }} is a two-credit course for students who are curious about
  computer science and have <strong>little or no prior programming experience</strong>. No coding
  background is assumed, and everyone is welcome.
</p>

<p>
  Throughout the semester, you will progress from writing your first line of Python code to
  creating a project of your own. You will learn foundational programming concepts — including
  variables, conditionals, loops, lists, dictionaries, and functions — while developing practical
  skills in reading, writing, and debugging programs. By hearing from current CS majors and
  computing professionals, you will also discover the many ways people study and apply computer
  science. By the end of the course, you will have a strong foundation in Python, a broader
  understanding of the field, and the confidence to continue exploring computer science.
</p>

{%- comment -%}
  The card is a <div> (not one big <a>) so it can hold both the note and the
  Past-syllabi disclosure — a <details> can't live inside an <a>. Published =
  syllabus_url is set AND syllabus_published is true; otherwise show "coming
  soon" copy but no live current-term link.
{%- endcomment -%}
{%- assign syllabus_ready = false -%}
{%- if course.syllabus_published and course.syllabus_url and course.syllabus_url != "" and course.syllabus_url != "TODO" -%}{%- assign syllabus_ready = true -%}{%- endif -%}
<div class="syllabus-card{% unless syllabus_ready %} syllabus-card--pending{% endunless %}">
  <span class="syllabus-card__title">📄 Course syllabus</span>
  {% if syllabus_ready %}
  <span class="syllabus-card__note"><a href="{{ course.syllabus_url }}">Read the full syllabus for {{ course.term }} →</a></span>
  {% else %}
  <span class="syllabus-card__note">The {{ course.term }} syllabus is being finalized. Once it's ready, it will be posted here.</span>
  {% endif %}
  {% if site.data.course.past_syllabi and site.data.course.past_syllabi != empty %}
  <details class="syllabus-past">
    <summary>Past syllabi</summary>
    <div class="syllabus-btns">
      {% for s in site.data.course.past_syllabi %}
      <a class="syllabus-btn" href="/assets/syllabi/{{ s.file }}">{{ s.term }}</a>
      {% endfor %}
    </div>
  </details>
  {% endif %}
</div>

## Course components


<div class="table-wrap" markdown="1">

| Component | Grade | What it is |
|---|---:|---|
| Attendance | 3% | Graded on 9 of 11 classes (2 absences are dropped). |
| Labs | 14% | Group work in the second half of class: a coding portion plus a worksheet. |
| Quizzes | 5% | Taken in class on PrairieLearn; your 2 lowest scores are dropped. |
| Homework | 28% | Weekly assignments that reinforce the previous lecture. |
| CS interview | 10% | Interview someone further along in CS and write a short reflection. |
| Final project | 25% | In groups, code a game and present on an intermediate CS topic. |
| CS engagement points | 15% | Points for class activities (office hours, course evals) and beyond (a CS student-org event, reading a CS book). Each point = 1% of your grade. |

</div>

<p class="note">See what a typical week looks like on the <a href="/schedule/">Schedule</a> page.</p>

## Quick links for current students

{% assign home_links = site.data.course.links | where: "home", true %}
{% include link-cards.html items=home_links %}

<p class="note">More, including Python references, on the <a href="/resources/">Resources</a> page.</p>
