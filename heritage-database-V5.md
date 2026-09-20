---
title: "Heritage Database"
layout: single
permalink: /heritage-database/
toc: false
sidebar:
  nav: "fieldwork-categories"
---

## Archive Overview

This database documents historical and heritage sites visited across China through longitudinal field research.

<div class="archive-overview">

<div class="overview-item">
<strong>75</strong>
<span>Documented Sites</span>
</div>

<div class="overview-item">
<strong>6</strong>
<span>Site Categories</span>
</div>

<div class="overview-item">
<strong>8</strong>
<span>Research Lenses</span>
</div>

</div>

---

## Interactive Map

Explore the geographical distribution of my fieldwork sites across China.

<div id="heritage-map" style="height:600px;width:100%;"></div>

<p class="map-note">
Map visualization based on documented heritage sites in the fieldwork archive.
</p>

---

## Browse Archive

Filter documented sites by category, historical period, and research lens.

<div class="archive-filters">

<label>
Category
<select id="category-filter">
<option value="">All Categories</option>
{% for category in site.data.fieldwork.categories %}
<option value="{{ category }}">{{ category }}</option>
{% endfor %}
</select>
</label>

<label>
Period
<select id="period-filter">
<option value="">All Periods</option>
{% assign periods = site.data.fieldwork.sites | map: "period" | flatten | uniq | sort %}
{% for period in periods %}
<option value="{{ period }}">{{ period }}</option>
{% endfor %}
</select>
</label>

<label>
Research Lens
<select id="lens-filter">
<option value="">All Research Lenses</option>
{% for lens in site.data.fieldwork.research_lenses %}
<option value="{{ lens }}">{{ lens }}</option>
{% endfor %}
</select>
</label>

</div>

<div id="site-count">
Showing {{ site.data.fieldwork.sites | size }} sites
</div>

---

## Site Catalogue

<div id="site-catalogue">

{% for item in site.data.fieldwork.sites %}

<article class="heritage-site"
data-category="{{ item.category.primary }}"
data-period="{{ item.period | join: '|' }}"
data-lens="{{ item.research_lens | join: '|' }}">

<h3>{{ item.name_en }}</h3>

<p>{{ item.name_zh }}</p>

<p><strong>Location:</strong> {{ item.location.city }}, {{ item.location.province }}</p>

<p><strong>Category:</strong> {{ item.category.primary }}</p>

<p><strong>Period:</strong> {{ item.period | join: ", " }}</p>

<p><strong>Research Themes:</strong> {{ item.research_lens | join: " · " }}</p>

</article>

{% endfor %}

</div>

<script>

document.addEventListener("DOMContentLoaded", function(){

const map = L.map('heritage-map');

L.tileLayer(
'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
{
attribution:'&copy; OpenStreetMap contributors'
}
).addTo(map);

let markers=[];

{% for item in site.data.fieldwork.sites %}
{% if item.location.latitude and item.location.longitude %}

let marker{{ forloop.index }} = L.marker([
{{ item.location.latitude }},
{{ item.location.longitude }}
])
.addTo(map)
.bindPopup(
"<strong>{{ item.name_en }}</strong><br>{{ item.name_zh }}<br>{{ item.location.city }}, {{ item.location.province }}"
);

markers.push(marker{{ forloop.index }});

{% endif %}
{% endfor %}

if(markers.length > 0){
map.fitBounds(
L.featureGroup(markers).getBounds(),
{padding:[40,40]}
);
}

});

</script>
