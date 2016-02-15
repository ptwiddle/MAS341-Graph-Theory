---
layout: page
title: Notes
permalink: /Notes/
---

This page contains links to the lecture notes for the course.

[Lecture notes from a previous year.](../OldLectureNotes.pdf)
These are a slightly skeletal, and may not match *exactly* with what we cover, but they won't be too far off and may be useful.

Each day of lecture will have its own page.  This will contain brief notes on the material covered, links to any slides I used and to other resources, and practice and challenge problems.

Each lecture will have have a comment thread to ask questions and further discuss the material.  


{% for lecture in site.lecturenotes %}
 - <a href="{{ lecture.url | prepend:site.baseurl }}"> {{ lecture.title }}</a>
{% endfor %} 

