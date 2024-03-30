---
layout: archive
title: " 📜 Publications"
permalink: /publications/
author_profile: false
---

layout: archive title: "📜 Publications" permalink: /publications/ author_profile: false
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/css/all.min.css">
{% if author.googlescholar %}

<section> <h2>Google Scholar</h2> <p>Find my complete list of publications on my <a href="{{author.googlescholar}}" target="_blank" rel="noopener noreferrer">Google Scholar profile</a>.</p> </section> {% endif %}
{% include base_path %}

<section> {% for post in site.publications reversed %} {% if post.published %} {% include archive-single-pubs.html %} {% endif %} {% endfor %} </section>
{% assign accepted_exists = false %}
{% for post in site.publications %}
{% if post.accepted %}
{% assign accepted_exists = true %}
{% endif %}
{% endfor %}

{% if accepted_exists %}

<section> <h2>Accepted Publications</h2> {% for post in site.publications reversed %} {% if post.accepted %} {% include archive-single-pubs.html %} {% endif %} {% endfor %} </section> {% endif %}