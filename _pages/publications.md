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


{% assign publication_years = '' %}
{% for post in site.publications %}
  {% assign year = post.date | date: '%Y' %}
  {% unless publication_years contains year %}
    {% assign publication_years = publication_years | append: year | append: ',' %}
  {% endunless %}
{% endfor %}


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



<canvas id="publicationsChart" width="400" height="400"></canvas>
<script>
  document.addEventListener('DOMContentLoaded', function () {
    var ctx = document.getElementById('publicationsChart').getContext('2d');
    var publicationYears = [];
    var publicationCounts = {};

    {% for post in site.publications %}
      var year = "{{ post.date | date: '%Y' }}";
      if (!publicationYears.includes(year)) {
        publicationYears.push(year);
        publicationCounts[year] = 0;
      }
      publicationCounts[year]++;
    {% endfor %}

    var data = {
      labels: publicationYears,
      datasets: [{
        label: 'Number of Publications',
        backgroundColor: 'rgb(255, 99, 132)',
        borderColor: 'rgb(255, 99, 132)',
        data: Object.values(publicationCounts),
      }]
    };

    var chart = new Chart(ctx, {
      type: 'line', // Change to 'bar', 'line', etc.
      data: data,
      options: {}
    });
  });
</script>