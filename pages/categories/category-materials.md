---
title: "Materials"
layout: archive
permalink: categories/materials
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Materials %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}