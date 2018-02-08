---
layout: page
title: Bulletins
permalink: /Bulletins/
---

Every week will have a bulletin page, containing a brief summary of the material covered this week, links to the slides and any other resources, a discussion thread, etc.

{% for bulletin in site.bulletins %}
 - <a href="{{ bulletin.url | prepend:site.baseurl }}"> {{ bulletin.title }}</a>
{% endfor %} 
