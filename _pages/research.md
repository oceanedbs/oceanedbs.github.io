---
layout: page
title: Research
permalink: /research/
title: research
description: 
nav: true
nav_order: 1
---

### _How can wearable robots become safer, more intuitive, and truly adapted to their users?_

Wearable robots, such as exoskeletons and prostheses, are increasingly used in rehabilitation and industrial contexts. They are designed to restore movement, reduce physical effort, and prevent musculoskeletal disorders. Yet their adoption remains limited, not only because of comfort or mechanical constraints, but also because these devices still struggle to adapt to the way humans actually move, learn, and change their motor strategies over time.

A major challenge is that human movement is redundant: the same hand trajectory can be achieved through many different combinations of shoulder, elbow, trunk, and muscle coordination. As a result, an exoskeleton may appear to preserve task performance while still modifying the user’s joint coordination or muscle activity. My previous work showed that these modifications can persist even after the device is removed, especially after repeated use, and that the type of robotic assistance can influence whether these new motor behaviors are retained or washed out.

This question is crucial because retention does not have the same meaning in all contexts. In rehabilitation, retaining a new motor strategy can be beneficial if it supports functional recovery. In industry, however, persistent changes in movement patterns may be undesirable, especially if workers are expected to return to their natural coordination after removing the exoskeleton. Understanding when, how, and why these adaptations emerge is therefore essential for designing safer wearable robots.

The aim of my research is to bridge human motor control and wearable robotics by studying how users adapt to exoskeletons across different timescales: the first minutes of interaction, stabilized use, and the period after device removal. I combine experimental analysis of movement, muscle activity, and inter-joint coordination with computational models of motor control, including inverse optimal control and learning-based approaches. These models will then be used to develop adaptive controllers able to adjust assistance in real time according to the user’s motor state.

Ultimately, I hope to contribute to the development of wearable robots that do more than assist movement mechanically: devices that understand, predict, and guide human adaptation. Such systems could promote useful motor learning in rehabilitation, limit unwanted long-term changes in industrial settings, and support safer, more personalized, and more effective human–robot interaction.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/paexo.webp" title="Paexo" width="600" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

---

<h2> Last Posts about my research  </h2>

<ul>
 {% if page.pagination.enabled %}
      {% assign postlist = paginator.posts %}
    {% else %}
      {% assign postlist = site.posts %}
    {% endif %}

{% for post in site.categories.research %}

    {% if post.external_source == blank %}
      {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
    {% else %}
      {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
    {% endif %}
    {% assign year = post.date | date: "%Y" %}
    {% assign tags = post.tags | join: "" %}
    {% assign categories = post.categories | join: "" %}

    {% if post.thumbnail %}

<div class="row">
          <div class="col-sm-9">
{% endif %}
        <h3>
        {% if post.redirect == blank %}
          <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
        {% elsif post.redirect contains '://' %}
          <a class="post-title" href="{{ post.redirect }}" target="_blank">{{ post.title }}</a>
          <svg width="2rem" height="2rem" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
            <path d="M17 13.5v6H5v-12h6m3-3h6v6m0-6-9 9" class="icon_svg-stroke" stroke="#999" stroke-width="1.5" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round"></path>
          </svg>
        {% else %}
          <a class="post-title" href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
        {% endif %}
      </h3>
      <p>{{ post.description }}</p>
      <p class="post-meta">
        {{ read_time }} min read &nbsp; &middot; &nbsp;
        {{ post.date | date: '%B %d, %Y' }}
        {% if post.external_source %}
        &nbsp; &middot; &nbsp; {{ post.external_source }}
        {% endif %}
      </p>
      <p class="post-tags">
        <a href="{{ year | prepend: '/blog/' | prepend: site.baseurl}}">
          <i class="fa-solid fa-calendar fa-sm"></i> {{ year }} </a>

          {% if tags != "" %}
          &nbsp; &middot; &nbsp;
            {% for tag in post.tags %}
            <a href="{{ tag | slugify | prepend: '/blog/tag/' | prepend: site.baseurl}}">
              <i class="fa-solid fa-hashtag fa-sm"></i> {{ tag }}</a> &nbsp;
              {% endfor %}
          {% endif %}

          {% if categories != "" %}
          &nbsp; &middot; &nbsp;
            {% for category in post.categories %}
            <a href="{{ category | slugify | prepend: '/blog/category/' | prepend: site.baseurl}}">
              <i class="fa-solid fa-tag fa-sm"></i> {{ category }}</a> &nbsp;
              {% endfor %}
          {% endif %}
    </p>

{% if post.thumbnail %}

</div>

  <div class="col-sm-3">
    <img class="card-img" src="{{post.thumbnail | relative_url}}" style="object-fit: cover; height: 90%" alt="image">
  </div>
</div>
{% endif %}
      {% endfor %}

  </ul>

{% if page.pagination.enabled %}
{% include pagination.liquid %}
{% endif %}
