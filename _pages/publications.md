---
layout: archive
title: " 📜 Publications"
permalink: /publications/
author_profile: false
---

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

{% if author.googlescholar %}
  <section>
    <h2>Google Scholar</h2>
    <p>Find my complete list of publications on my <a href="{{author.googlescholar}}" target="_blank" rel="noopener noreferrer">Google Scholar profile</a>.</p>
  </section>
{% endif %}

{% include base_path %}



<section>
  {% for post in site.publications reversed %}
    {% if post.published %} 
       {% include archive-single-pubs.html %}
    {% endif %}
  {% endfor %}
</section>

{% assign accepted_exists = false %}
{% for post in site.publications %}
  {% if post.accepted %}
    {% assign accepted_exists = true %}
  {% endif %}
{% endfor %}

{% if accepted_exists %}
  <section>
    <h2>Accepted Publications</h2>
    {% for post in site.publications reversed %}
      {% if post.accepted %} 
         {% include archive-single-pubs.html %}
      {% endif %}
    {% endfor %}
  </section>
{% endif %}


