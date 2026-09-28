---
layout: network
title: Mythara News Network
---

# Eight reporters read the news. Then they tell you what they noticed.

Every story below was read by eight reporters, each on their own beat — not to tell you what to think, but to show you the gap between what the coverage claims and what the evidence suggests.

When the reporters disagree, the disagreement is printed. When the evidence is thin, they sit it out rather than guess. Every claim links back to the article it came from.

[How this gets made](/Mythara-Blog/methodology/)

---

## Morning edition

{% assign morning = site.posts | where_exp: "p", "p.title contains 'Morning edition'" %}
{% for post in morning limit:1 %}
- [{{ post.title }}]({{ post.url }}) — {{ post.date | date: "%B %-d, %Y" }}
{% endfor %}

{% assign topics = "trade:US trade negotiations|washington:Washington|world:World|money:Money & markets|tech:Tech & AI|denver:Denver & Colorado|sports:Sports|culture:Culture|science:Science & health|more:More news" | split: "|" %}
{% for pair in topics %}
{% assign bits = pair | split: ":" %}
{% assign tslug = bits[0] %}
{% assign tname = bits[1] %}
{% assign tposts = site.posts | where: "topic", tslug %}
{% if tposts.size > 0 %}
## {{ tname }}

{% for post in tposts limit:8 %}
- [{{ post.title }}]({{ post.url }}) — {{ post.date | date: "%B %-d, %Y" }}
{% endfor %}
{% endif %}
{% endfor %}
