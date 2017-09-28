---
layout: page
title: Archive
---

### Blog Posts

{% for post in site.posts %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}



### DL In Finance Paper Summaries

{% for summary in site.summaries %}
  * [ {{ summary.title }} ](/deep_learning_in_finance/#{{ summary.pid }})
{% endfor %}
