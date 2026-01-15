---
layout: default
title: Čeština – vyber ročník
---

# Čeština

Vyber ročník, který chceš procvičovat:

<ul class="grade-list">
  {% for i in (1..9) %}
    <li><a href="/cestina/{{ i }}.trida/">{{ i }}. třída</a></li>
  {% endfor %}
  <li><a href="/cestina/stredni/">Střední škola</a></li>
</ul>

<style>
  .grade-list {
    list-style: none;
    padding: 0;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 20px;
  }
  .grade-list li a {
    display: block;
    background: #2196F3;
    color: white;
    padding: 25px;
    text-align: center;
    font-size: 22px;
    border-radius: 10px;
    text-decoration: none;
  }
  .grade-list li a:hover {
    background: #0b7dda;
  }
</style>
