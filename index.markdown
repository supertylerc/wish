---
layout: default
title: Wishlist
---
* TOC
{:toc}

{% for wishes in site.data.wishes %}
### {{ wishes[0] | capitalize }} ###
{% for w in wishes[1] %}
{% assign price = w.price | to_integer %}
{{ price }}
{{ w.price }}
{% case price %}
  {% when <= 50 %}
    {% assign price_class = "btn btn-block btn-sm btn-success" %}
  {% when <= 125 %}
    {% assign price_class = "btn btn-block btn-sm btn-warning" %}
  {% when > 125 %}
    {% assign price_class = "btn btn-block btn-sm btn-danger" %}
  {% else %}
    {% assign price_class = "btn btn-block btn-sm btn-default" %}
{% endcase %}
<div class="tile" markdown="1">
#### {{ w.title | smartify }} {% if w.price %}<span class="{{ price_class }}" style="white-space:nowrap">**${{ w.price }}**</span>{% endif %} ####

{% if w.image %}![Image for {{ w.title | smartify }}]({{ w.image }}){% endif %}

{% if w.link %}
<span>{% for l in w.link %}[[{{ l[0] | replace:"_"," " | capitalize }}]({{ l[1] }})]{% if forloop.length > 1 and forloop.last == false %} / {% endif %}{% endfor %}</span>
{% endif %}
</div>
{% endfor %}
{% endfor %}
