---
title: "MaVILab - Team"
subtitle: "Team"
layout: gridlay
excerpt: "MaVILab: Team members"
sitemap: false
permalink: /team/
---

# Group Members

 **We are  looking for new students to join the team!**


<!-- Jump to [staff](#staff), [master and bachelor students](#master-and-bachelor-students), [alumni](#alumni), [administrative support](#administrative-support), [lab visitors](#lab-visitors). -->

<div class="row" style="margin-left:0px;">
## Faculty
{% assign number_printed = 0 %}

{% for member in site.data.team_members %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" width="25%" style="float: left" />
  <h4>{{ member.name }} {% if member.homepage %}<a href="{{ member.homepage }}" title="Link to member homepage"><i class="fa fa-home fa-fw" aria-hidden="true"></i></a>{% endif %} {% if member.github %}<a href="{{ member.github }}" title="Link to member github"><i class="fa fa-github fa-fw" aria-hidden="true"></i></a>{% endif %} </h4>
  
  <i>{{ member.info }} </i>
  <ul style="overflow: hidden">

  {% if member.number_educ == 1 %}
  <li> {{ member.education1 }} </li>
  {% endif %}

  {% if member.number_educ == 2 %}
  <li> {{ member.education1 }} </li>
  <li> {{ member.education2 }} </li>
  {% endif %}

  {% if member.number_educ == 3 %}
  <li> {{ member.education1 }} </li>
  <li> {{ member.education2 }} </li>
  <li> {{ member.education3 }} </li>
  {% endif %}

  {% if member.number_educ == 4 %}
  <li> {{ member.education1 }} </li>
  <li> {{ member.education2 }} </li>
  <li> {{ member.education3 }} </li>
  <li> {{ member.education4 }} </li>
  {% endif %}

  </ul>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}
</div>



<!-- Students -->

{% for types in site.data.students_list %}

{% if types.type == "Students" %}
<div class="row"  style="margin-left:0px;">
<h2>{{ types.type }}</h2>


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
  <ul style="overflow: hidden">
 
  <li> Since: {{ member.since }} </li>

  </ul>
</div>


{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

</div>


{% elsif types.type == "Alumini" %}

<div class="row"  style="margin-left:0px;">
<h2>{{ types.type }}</h2>

{% assign number_printed = 0 %}

{% for member in types.list %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" width="15%" style="float: left" />
  <h4>{{ member.name }} {% if member.homepage %}<a href="{{ member.homepage }}" title="Link to member homepage"><i class="fa fa-home fa-fw" aria-hidden="true"></i></a>{% endif %} {% if member.github %}<a href="{{ member.github }}" title="Link to member github"><i class="fa fa-github fa-fw" aria-hidden="true"></i></a>{% endif %} </h4>
  
  <p>
  Role: {{ member.level }}  
  Period: {{ member.since }} -{% if member.until %} {{ member.until }} {% else %} Today {% endif %} </p> 
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

</div>


{% endif %}

{% endfor %}