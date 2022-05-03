---
layout: default
title: Wishlist
---
* TOC
{:toc}

{% for wishes_map in site.data.wishes %}
### {{ wishes_map[0] | capitalize }} ###
{% assign wishes = wishes_map[1] | sort: "price" %}
{% for w in wishes %}
{% assign price = w.price | to_integer %}
{% if price <= 50 %}
  {% assign price_class = "btn btn-block btn-xs btn-success" %}
{% elsif price <= 125 %}
  {% assign price_class = "btn btn-block btn-xs btn-warning" %}
{% elsif price > 125 %}
  {% assign price_class = "btn btn-block btn-xs btn-danger" %}
{% else %}
  {% assign price_class = "btn btn-block btn-xs btn-default" %}
{% endif %}
<div class="tile" markdown="1">
#### {{ w.title | smartify }} {% if w.price %}<span class="{{ price_class }}" style="white-space:nowrap">**${{ w.price }}**</span>{% endif %} ####

{% if w.image %}![Image for {{ w.title | smartify }}]({{ w.image }}){% endif %}

{% if w.link %}
<span>{% for l in w.link %}[[{{ l[0] | replace:"_"," " | capitalize }}]({{ l[1] }})]{% if forloop.length > 1 and forloop.last == false %} / {% endif %}{% endfor %}</span>
{% endif %}
</div>
{% endfor %}
{% endfor %}
