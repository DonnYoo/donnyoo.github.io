---
title: "Hair"
layout: archive
permalink: categories/hair
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Hair %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}