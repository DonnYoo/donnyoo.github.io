---
title: "Movie Sentence"
layout: archive
permalink: categories/moviesentence
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Movie %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}