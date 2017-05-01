---
layout: page
title: Notes
permalink: /Notes/
---

This page contains links to the lecture notes for the course.

<a href="../lecturenotes/lecturenotes.pdf"> Lecture notes as a pdf </a>

[Lecture notes from a previous year.](../OldLectureNotes.pdf)
These are a bit skeletal, and do not match *exactly* what we cover, but they're very close and you may find them useful.

Each day of lecture will have its own page.  This will contain brief notes on the material covered and links to any slides I used in lecture.

Each lecture will have have a comment thread to ask questions and further discuss the material.  


{% for lecture in site.lecturenotes %}
 - <a href="{{ lecture.url | prepend:site.baseurl }}"> {{ lecture.title }}</a>
{% endfor %} 

