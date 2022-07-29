---
title: Gallo's musings
future: false
layout: collection
permalink: /blog/
collection: blog
entries_layout: grid
classes: wide
sort_order: reverse
header:
  overlay_image: /images/blog.png
  overlay_filter: 0.5
excerpt: "and off-the-rails-train-of-thought thoughts"
---
{% capture written_label %}'None'{% endcapture %}

{% for collection in site.collections %}
  {% unless collection.output == false or collection.label == "blog" %}
    {% capture label %}{{ collection.label }}{% endcapture %}
    {% if label != written_label %}
      <h2 id="{{ label | slugify }}" class="archive__subtitle">{{ label }}</h2>
      {% capture written_label %}{{ label }}{% endcapture %}
    {% endif %}
  {% endunless %}
  {% for post in collection.docs %}
    {% unless collection.output == false or collection.label == "blog" %}
      {% include archive-single.html %}
    {% endunless %}
  {% endfor %}
{% endfor %}
