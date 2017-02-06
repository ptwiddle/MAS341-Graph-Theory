---
layout: page
title: Problems
permalink: /Problems/
---

This page will host example problems, problems to be handed in, proofs from lecture that will be valid for examination, etc.

Problem Sets and Solutions
====

{% for problemsheet in site.practiceproblems %}
 - <a href="{{ problemsheet.url | prepend:site.baseurl }}"> {{ problemsheet.title }}</a>
{% endfor %} 

