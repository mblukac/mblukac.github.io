---
layout: archive
title: ""
permalink: /publications/
author_profile: true
---

## Publications

***

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}


## Working papers

***

{% include base_path %}

{% for post in site.portfolio reversed %}
  {% include archive-single.html %}
{% endfor %}

<br>
<br>
