---
layout: network
title: Mythara News Network
---

# Eight reporters read the morning news. Then they tell you what the coverage is hiding.

Every story below was read by eight reporters, each on their own beat. They point at what's actually happening, name the shadow intent — the hidden motive the coverage is serving — and spell out what it means for real people: who gets helped and who gets hurt.

The lens stays aimed at the seats of power: public figures, institutions, the people making the decisions. Never private citizens.

When the reporters disagree, the disagreement is printed. When the evidence is thin, they sit it out rather than guess. Every claim links back to the article it came from, and sourced facts are never mixed with reporter inference.

[How this gets made](/Mythara-Blog/methodology/)

---

## Morning edition

{% assign morning = site.posts | where_exp: "p", "p.title contains 'Morning edition'" %}
{% for post in morning limit:1 %}
- [{{ post.title }}]({{ post.url | relative_url }}) — {{ post.date | date: "%B %-d, %Y" }}
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
- [{{ post.title }}]({{ post.url | relative_url }}) — {{ post.date | date: "%B %-d, %Y" }}
{% endfor %}
{% endif %}
{% endfor %}
