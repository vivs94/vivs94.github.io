---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: false
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% if post.published %} 
     {% include archive-single.html %}
  {% endif %}
{% endfor %}

Publication Accepted
==

{% for post in site.publications reversed %}
  {% if post.accepted %} 
     {% include archive-single.html %}
  {% endif %}
{% endfor %}


Upcoming Work
==

{% for post in site.publications reversed %}
  {% if post.underreview %} 
     {% include archive-single.html %}
  {% endif %}
{% endfor %}