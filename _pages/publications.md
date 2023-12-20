---
layout: archive
title: " 📜 Publications"
permalink: /publications/
author_profile: false
---


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


{% assign collaborator_counts = hash %}

{% for post in site.publications %}
  {% for author in post.authors %}
    {% unless author == 'Hardik Prabhu' %}
      {% if collaborator_counts[author] %}
        {% assign collaborator_counts = collaborator_counts | merge:  {author => collaborator_counts[author] | plus: 1} %}
      {% else %}
        {% assign collaborator_counts = collaborator_counts | merge:  {author => 1} %}
      {% endif %}
    {% endunless %}
  {% endfor %}
{% endfor %}

{% assign collaborators = collaborator_counts | map %}
{% assign sorted_collaborators = collaborators | sort: '1' | reverse %}

<section>
  <h2>Collaborators</h2>
  <ul id="collaborators-list">
    {% for item in sorted_collaborators %}
      <li>{{ item[0] }} ({{ item[1] }} collaborations)</li>
    {% endfor %}
  </ul>
</section>