---
title: "MaVILab - Publications"
subtitle: "Publications"
layout: gridlay
excerpt: "MaVILabb -- Publications."
sitemap: false
permalink: /publications/
---


# Publications

<!-- ## Group highlights -->

<p> &nbsp; </p>

{% for years in site.data.pub_list %}
<h4>{{ years.year }}</h4>

{% for publi in years.pubs %}
<p>
<strong>{{ publi.title }}</strong> <br />
<em>{{ publi.authors }} </em><br />
{{ publi.media }}<br />
{% if publi.links.doi %}
<a href="{{ publi.links.doi }}" title="Link to DOI of the publication"><i class="ai ai-fw ai-doi" aria-hidden="true"></i></a> &nbsp;
{% endif %}
{% if publi.links.youtube %}
<a href="{{ publi.links.youtube }}" title="Link to YouTube work video"> <i class="fa fa-youtube fa-1x" aria-hidden="true"></i></a> &nbsp;
{% endif %}
{% if publi.links.github  %}
<a href="{{ publi.links.github }}" title="Link to GitHub work project"><i class="fa fa-github fa-1x" aria-hidden="true"></i></a> &nbsp;
{% endif %}
{% if publi.links.arxiv %}
<a href="{{ publi.links.arxiv }}" title="Link to ArXiv publication"><i class="ai ai-fw ai-arxiv" aria-hidden="true"></i></a> &nbsp;
{% endif %}
{% if publi.links.url %}
<a href="{{ publi.links.url }}" title="Link to official work website"><i class="fa fa-fw fa-link" aria-hidden="true"></i></a> &nbsp;
{% endif %}
</p>

{% endfor %}
{% endfor %}