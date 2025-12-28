---
layout: page
title: Commute-Log
permalink: /commute-log/
---

---
layout: page
title: Commute-Log
permalink: /commute-log/
---

<p class="commute-desc">
  Short daily notes from my commute—raw thoughts, questions, and small reflections.
</p>

{% assign logs = site.commute_log | sort: "date" | reverse %}

{% assign all_tags = "" | split: "" %}
{% for item in logs %}
  {% for t in item.tags %}
    {% unless all_tags contains t %}
      {% assign all_tags = all_tags | push: t %}
    {% endunless %}
  {% endfor %}
{% endfor %}
{% assign all_tags = all_tags | sort %}

<div class="tag-filter">
  <a href="#" class="tag-pill is-active" data-tag="all">All</a>
  {% for t in all_tags %}
    <a href="#" class="tag-pill" data-tag="{{ t | escape }}">{{ t }}</a>
  {% endfor %}
</div>

<ul class="commute-list">
  {% for item in logs %}
    <li class="commute-item" data-tags="{{ item.tags | join: ',' | escape }}">
      <a href="{{ item.url | relative_url }}">{{ item.title }}</a>
      <span> — {{ item.date | date: "%Y-%m-%d" }}</span>

      {% if item.tags and item.tags.size > 0 %}
        <span class="commute-tags">
          / {% for t in item.tags %}
              <span class="tag-name">{{ t }}</span>{% unless forloop.last %}, {% endunless %}
            {% endfor %}
        </span>
      {% endif %}
    </li>
  {% endfor %}
</ul>

<script>
(function () {
  const pills = document.querySelectorAll('.tag-pill');
  const items = document.querySelectorAll('.commute-item');

  function setActive(tag) {
    pills.forEach(p => p.classList.toggle('is-active', p.dataset.tag === tag));
    items.forEach(li => {
      const tags = (li.dataset.tags || '').split(',').map(s => s.trim()).filter(Boolean);
      li.style.display = (tag === 'all' || tags.includes(tag)) ? '' : 'none';
    });
  }

  pills.forEach(p => {
    p.addEventListener('click', (e) => {
      e.preventDefault();
      const tag = p.dataset.tag;
      setActive(tag);

      // Optional: keep filter state in URL hash (shareable)
      if (tag === 'all') history.replaceState(null, '', location.pathname);
      else history.replaceState(null, '', location.pathname + '#tag=' + encodeURIComponent(tag));
    });
  });

  // If someone opens /commute-log/#tag=philosophy
  const m = location.hash.match(/tag=([^&]+)/);
  if (m) setActive(decodeURIComponent(m[1]));
})();
</script>


