---
layout: default
title: FAQ
permalink: /faq/
---

{%- comment -%}
  Instructor = the staff entry whose role is "Instructor" (fall back to the first
  entry). Only the instructor name/email below are data-driven; the Q&A copy is
  stable course policy and lives in this page body. The Thanksgiving question is
  gated to fall terms via course.term_season.
{%- endcomment -%}
{%- assign course = site.data.course.course -%}
{%- assign instructor = site.data.course.staff | where: "role", "Instructor" | first -%}
{%- unless instructor -%}{%- assign instructor = site.data.course.staff | first -%}{%- endunless -%}
{%- assign instructor_first = instructor.name | split: " " | first -%}

# Frequently asked questions

<div class="faq">

<details class="faq-item">
<summary>I've never taken computer science before and don't really know what CS or programming is. Will I be prepared for this course?</summary>
<div class="faq-answer" markdown="1">
Absolutely. This course assumes no prior exposure to computer science or programming. We'd love to
have you!
</div>
</details>

<details class="faq-item">
<summary>Can I take EECS 110 at the same time as EECS 183 or ENGR 101?</summary>
<div class="faq-answer" markdown="1">
Yes. There will be some overlap in programming concepts, though possibly in a different
language depending on the course. EECS 110 additionally offers ways to explore future CS pathways
through an undergraduate student panel, a Q&A with a CS faculty member, an interview assignment, and
a tour of a local software company.
</div>
</details>

<details class="faq-item">
<summary>Can I take EECS 110 if I have credit for EECS 280 or EECS 281?</summary>
<div class="faq-answer" markdown="1">
Congratulations, you're well on your way to mastering the fundamentals! Unfortunately, you may not
take EECS 110 if you already have credit for EECS 280 or EECS 281.
</div>
</details>

<details class="faq-item">
<summary>The semester has already started. Is it too late to join?</summary>
<div class="faq-answer" markdown="1">
If the add/drop deadline hasn't passed and seats are open, we encourage you to enroll through
[Wolverine Access](https://wolverineaccess.umich.edu). Please email {{ instructor_first }} to let us
know you've enrolled — especially if the semester is well underway — so we can help you get caught up
quickly. You won't be penalized for classes missed before you joined, and we'll set reasonable
deadlines for making up any work.
</div>
</details>

<details class="faq-item">
<summary>Are there any required books or materials?</summary>
<div class="faq-answer" markdown="1">
No, all you need is a laptop.
</div>
</details>

<details class="faq-item">
<summary>Can I use generative AI tools like ChatGPT on assignments?</summary>
<div class="faq-answer" markdown="1">
To use generative AI tools responsibly and effectively, you need a strong mastery of the fundamental
concepts and skills in a discipline. For that reason, generative AI tools are not permitted in this
course. During the term we briefly discuss how these tools work and why we don't permit them here.
If you have questions or get stuck, we always encourage you to post on Piazza (you may post
anonymously!) or stop by office hours.
</div>
</details>

<details class="faq-item">
<summary>Is in-person attendance required?</summary>
<div class="faq-answer" markdown="1">
EECS 110 is a collaborative course and students benefit from being together in the classroom, so
attendance is graded and counts for a small portion of the overall grade. Two attendance points are
dropped for every student to cover minor illness, job interviews, student-org commitments, or other
unexpected events. If a significant illness or event will cause you to miss multiple or consecutive
classes, please contact {{ instructor_first }} directly.
</div>
</details>

{% if course.term_season == "fall" %}
<details class="faq-item">
<summary>Is there class the week of Thanksgiving?</summary>
<div class="faq-answer" markdown="1">
There is no in-person class that week. Instead, {{ instructor_first }} meets with each final-project
group over Zoom at a time the group chooses. You do not need to be physically in Ann Arbor the week of
Thanksgiving for EECS 110.
</div>
</details>
{% endif %}

<details class="faq-item">
<summary>Is there a final exam?</summary>
<div class="faq-answer" markdown="1">
No. In place of a final exam, there is a final project with a coding portion and a presentation
delivered during the final class period. After that, there's no expectation that you remain in Ann
Arbor, *as long as your final-project group can reach you while you finalize your code submission.*
</div>
</details>

<details class="faq-item">
<summary>What is the median grade for the course?</summary>
<div class="faq-answer" markdown="1">
Our goal is to give every student the resources needed to demonstrate competency and earn an A. For
more information, including a historical grade breakdown, see the EECS 110 course page on
[Atlas](https://atlas.ai.umich.edu/courses/EECS110/2610/).
</div>
</details>

<details class="faq-item">
<summary>I'm facing a challenge that's interfering with my work in this course. What should I do?</summary>
<div class="faq-answer" markdown="1">
We're sorry you're going through this, and we want to help. Please email {{ instructor_first }} at
[{{ instructor.email }}](mailto:{{ instructor.email }}) or stop by office hours so we can best
support you — you are not alone. The University's
[Resource Navigators](https://campusinfo.umich.edu/resource-navigators) can also help you connect to
support. If you're feeling overwhelmed, depressed, or in need of support, services are available
through Counseling and Psychological Services ([CAPS](https://caps.umich.edu)) and
[UWill](https://umich.uwill.com). You may also find the well-being resources offered through the
Office of Student Life helpful. For an urgent matter when CAPS is closed, call 734-764-8312
(press 0) to reach CAPS After Hours.
</div>
</details>

<details class="faq-item">
<summary>I'm interested in being the GSI for this course. What should I do?</summary>
<div class="faq-answer" markdown="1">
EECS 110 is a unique course: it has a single GSI position, and that GSI is the instructor of record
and sole instructor for the course. The GSI is selected from applicants who list EECS 110 on the CSE
GSI application form, typically released a few months before the semester begins. If you are eager to
express your interest in being the instructor for EECS 110, we encourage you to fill out this
[interest form](https://forms.gle/o2bCrhdBU9icGRmEA). Note that EECS 110 instructors typically have
at least one prior semester of GSI experience.
</div>
</details>

<details class="faq-item">
<summary>I'm interested in being an IA or grader for this course. What should I do?</summary>
<div class="faq-answer" markdown="1">
Select EECS 110 on the IA or grader application form. We'll see your application, so there's no need
to email {{ instructor_first }}. Note that if enrollment doesn't meet a threshold, an IA or grader may not
be allocated for a given term; historically this has sometimes been the case in Winter, though every
semester is different.
</div>
</details>

<!-- PENDING (do not render): "Does EECS 110 count toward a CS major, minor, or any degree
     requirement?" — answer pending from the undergraduate advising office. Leave as this comment
     until confirmed, then add as a Q&A. -->

</div>
