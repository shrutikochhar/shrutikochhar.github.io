---
layout: archive
title: "PhD"
permalink: /phd/
author_profile: true
---

{% include base_path %}

{% for post in site.phd reversed %}
  {% include archive-single.html %}
{% endfor %}
