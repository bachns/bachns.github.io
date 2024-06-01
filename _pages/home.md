---
permalink: /
layout: single
author_profile: true
read_time: false
comments: false
header:
  image: /assets/images/about-me.jpg
---

Xin chào, tôi là Bách Nguyễn, tác giả của blog này. Rất vui vì bạn đã quan tâm đến hành trình tìm hiểu kiến thức của tôi.

<h3 class="archive__subtitle">{{ site.data.ui-text[site.locale].recent_posts | default: "Recent Posts" }}</h3>

{% if paginator %}
{% assign posts = paginator.posts %}
{% else %}
{% assign posts = site.posts %}
{% endif %}

{% assign entries_layout = page.entries_layout | default: 'list' %}

<div class="entries-{{ entries_layout }}">
  {% for post in posts %}
    {% include archive-single.html type=entries_layout %}
  {% endfor %}
</div>

{% include paginator.html %}
