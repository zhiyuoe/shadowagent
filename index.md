---
layout: default
title: Home
nav_order: 1
has_children: true
description: "Game description"
permalink: /
---


# Exploring reinforcement learning agents in game experience
{: .fs-9 }

Project Shadow Agent is an experimental project exploring new gameplay interactions using reinforcement learning. By working with Google Stadia, the team seeks new game genres and different potential applications. {: .fs-6 .fw-300 }

---

## About us
We are a team from [Entertainment Technology Center](http://www.etc.cmu.edu/), Carnegie Mellon, working with designers and machine learning engineers from [Google Stadia](https://github.com/pmarsceill/just-the-docs#contributing).

## Contributors

<ul class="list-style-none">
{% for contributor in site.github.contributors %}
  <li class="d-inline-block mr-1">
     <a href="{{ contributor.html_url }}"><img src="{{ contributor.avatar_url }}" width="32" height="32" alt="{{ contributor.login }}"/></a>
  </li>
{% endfor %}
</ul>
