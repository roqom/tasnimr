---
layout: page
title: Commute-Log
permalink: /commute-log/
---

<ul>
  {% assign logs = site.commute_log | sort: "date" | reverse %}
  {% for item in logs %}
    <li>
      <a href="{{ item.url | relative_url }}">{{ item.title }}</a>
      <span> — {{ item.date | date: "%Y-%m-%d" }}</span>
    </li>
  {% endfor %}
</ul>
