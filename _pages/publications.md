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


<section>
  <h2>Collaborators</h2>
  <ul id="collaborators-list">
    <!-- Collaborators will be listed here -->
  </ul>
</section>

<script>
  document.addEventListener('DOMContentLoaded', function () {
    var collaborators = {};

    {% for post in site.publications %}
      {% for author in post.authors %}
        {% unless author == 'Hardik Prabhu' %} // Replace 'Your Name' with your actual name
          if (!collaborators.hasOwnProperty('{{ author }}')) {
            collaborators['{{ author }}'] = 0;
          }
          collaborators['{{ author }}']++;
        {% endunless %}
      {% endfor %}
    {% endfor %}

    var sortedCollaborators = Object.keys(collaborators).sort(function(a, b) {
      return collaborators[b] - collaborators[a];
    });

    var collaboratorsList = document.getElementById('collaborators-list');
    sortedCollaborators.forEach(function(collaborator) {
      var li = document.createElement('li');
      li.textContent = collaborator + ' (' + collaborators[collaborator] + ')';
      collaboratorsList.appendChild(li);
    });
  });
</script>