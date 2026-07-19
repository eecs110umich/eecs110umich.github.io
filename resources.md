---
layout: default
title: Resources
permalink: /resources/
---

# Resources

Course links and additional Python resources.

## Course links

The online tools we use in EECS 110.

{% include link-cards.html items=site.data.course.links %}

## Python resources

Friendly, beginner-appropriate resources for assignment help and practicing outside of class.
Google Colab runs Python 3.12, so the official docs below point to the 3.12 documentation.
Remember to cite the source in a comment if you use an online page to help with a course
assignment.

{% assign pr = site.data.python_resources %}

<div class="pyres">

  <form class="pyres-filters" role="search" aria-label="Filter Python resources">
    <div class="pyres-search">
      <label for="pyres-search">Search by title</label>
      <input type="search" id="pyres-search" placeholder="e.g. loops, dictionaries, pandas…" autocomplete="off">
    </div>

    <fieldset class="pyres-facet">
      <legend>Filter by source</legend>
      {% for s in pr.sources %}
      <label><input type="checkbox" class="pyres-source" value="{{ s.id }}"> {{ s.label }}</label>
      {% endfor %}
    </fieldset>

    <fieldset class="pyres-facet">
      <legend>Filter by topic</legend>
      {% for t in pr.topics %}
      <label><input type="checkbox" class="pyres-topic" value="{{ t.id }}"> {{ t.label }}</label>
      {% endfor %}
    </fieldset>

    <button type="button" id="pyres-clear">Clear filters</button>
  </form>

  <p class="pyres-count" id="pyres-count" aria-live="polite" role="status"></p>

  <ul class="pyres-list">
    {% for r in pr.resources %}
    {%- assign src = pr.sources | where: "id", r.source | first -%}
    <li class="pyres-card" data-source="{{ r.source }}" data-topics="{{ r.topics | join: ' ' }}" data-title="{{ r.title | downcase | escape }}">
      <a class="pyres-card__title" href="{{ r.url }}" target="_blank" rel="noopener">{{ r.title }}</a>
      <p class="pyres-card__tags">
        <span class="pyres-badge">{{ src.label | default: r.source }}</span>
        {% for tid in r.topics %}{%- assign tobj = pr.topics | where: "id", tid | first -%}<span class="pyres-tag">{{ tobj.label | default: tid }}</span>{% endfor %}
      </p>
    </li>
    {% endfor %}
  </ul>

  <p class="pyres-empty" id="pyres-empty" hidden>No resources match those filters. Try clearing a filter or the search box.</p>
</div>

<script>
(function () {
  var root = document.querySelector('.pyres');
  if (!root) return;
  var cards   = Array.prototype.slice.call(root.querySelectorAll('.pyres-card'));
  var sources = Array.prototype.slice.call(root.querySelectorAll('.pyres-source'));
  var topics  = Array.prototype.slice.call(root.querySelectorAll('.pyres-topic'));
  var search  = root.querySelector('#pyres-search');
  var count   = root.querySelector('#pyres-count');
  var empty   = root.querySelector('#pyres-empty');
  var clear   = root.querySelector('#pyres-clear');
  var total   = cards.length;

  function checked(boxes) {
    return boxes.filter(function (b) { return b.checked; }).map(function (b) { return b.value; });
  }

  function apply() {
    var selSources = checked(sources);
    var selTopics  = checked(topics);
    var q = (search.value || '').trim().toLowerCase();
    var shown = 0;

    cards.forEach(function (card) {
      var cardSource = card.getAttribute('data-source');
      var cardTopics = card.getAttribute('data-topics').split(' ');
      var title = card.getAttribute('data-title');
      var okSource = selSources.length === 0 || selSources.indexOf(cardSource) !== -1;
      var okTopic  = selTopics.length === 0 || selTopics.some(function (t) { return cardTopics.indexOf(t) !== -1; });
      var okSearch = q === '' || title.indexOf(q) !== -1;
      var visible = okSource && okTopic && okSearch;
      card.hidden = !visible;
      if (visible) shown++;
    });

    count.textContent = 'Showing ' + shown + ' of ' + total + ' resources';
    empty.hidden = shown !== 0;
  }

  sources.concat(topics).forEach(function (b) { b.addEventListener('change', apply); });
  search.addEventListener('input', apply);
  clear.addEventListener('click', function () {
    sources.concat(topics).forEach(function (b) { b.checked = false; });
    search.value = '';
    apply();
  });

  apply();
})();
</script>
