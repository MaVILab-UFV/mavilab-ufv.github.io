---
title: "MaVILab - Expo Pinacoteca"
subtitle: "Expo Pinacoteca"
layout: gridlay
excerpt: "MaVILab -- Expo Pinacoteca"
sitemap: false
permalink: /pinacoteca-50-anos/transfer-style
---

# Pinacoteca UFV
## Exposição comemorativa de 50 anos
### Obra Digtial: Transferência de Estilo



<div class="row"  style="margin-left:0px;">

## Equipe:

{% for types in site.data.pinacoteca-50-anos %}

{% if types.type == "transfer" %}

{% assign number_printed = 0 %}

{% for member in types.list %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" width="15%" style="float: left" />
  <h4>{{ member.name }} {% if member.homepage %}<a href="{{ member.homepage }}" title="Link to member homepage"><i class="fa fa-home fa-fw" aria-hidden="true"></i></a>{% endif %} {% if member.github %}<a href="{{ member.github }}" title="Link to member github"><i class="fa fa-github fa-fw" aria-hidden="true"></i></a>{% endif %} </h4>
  
  <i>{{ member.level }} </i>

</div>


{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}
</div>

{% endif %}

{% endfor %}