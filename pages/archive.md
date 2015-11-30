---
layout: page
title: "Archive"
description: "All posts list"
tagline: "Intfr"
menu:
  name: Archive
  parent: main
  position: 200
---
{% include JB/setup %}
<ul class="posts">
  {% for post in site.posts %}
      <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
      <p><small><strong>{{ post.date | date: "%B %e, %Y" }}</strong> . {{ post.category }} . <a href="http://intfrr.github.com{{ post.url }}#disqus_thread"></a></small></p>
  {% endfor %}
</ul>
