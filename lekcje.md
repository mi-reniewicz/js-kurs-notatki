---
layout: page
title: Lekcje
permalink: /lekcje/
---

# 📘 Kurs JavaScript

<input type="text" id="searchInput" placeholder="Szukaj lekcji..." style="width: 100%; padding: 0.5rem; margin: 1rem 0;">

<ul>
  {% assign lessons = site.pages | where_exp: "page", "page.permalink contains '/lessons/'" | sort: "title" %}
  {% for lesson in lessons %}
    <li><a href="/js-kurs-notatki{{ lesson.url }}">{{ lesson.title }}</a></li>
  {% endfor %}
</ul>

<script>
document.getElementById("searchInput").addEventListener("input", function() {
  const filter = this.value.toLowerCase();
  document.querySelectorAll("#lessonList li").forEach(function(li) {
    const text = li.textContent.toLowerCase();
    li.style.display = text.includes(filter) ? "" : "none";
  });
});
</script>
