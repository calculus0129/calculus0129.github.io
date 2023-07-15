---
title: "Posts by Category"
layout: categories
permalink: /categories/
author_profile: true
sidebar_main: true
---
<!--{% assign posts = site.categories.study %}-->
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}