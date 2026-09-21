
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

<div class="archive-stats">

<div class="archive-stat">
<strong>75</strong>
<span>Documented Sites</span>
</div>

<div class="archive-stat">
<strong>4</strong>
<span>Site Categories</span>
</div>

<div class="archive-stat">
<strong>8</strong>
<span>Research Lenses</span>
</div>

</div>

---

## Interactive Map

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<div id="heritage-map" style="height:600px;width:100%;"></div>

---

## Browse Archive

<div class="archive-filters">

<select id="category-filter">
<option value="">All Categories</option>
<option value="Tombs & Mausoleums">Tombs & Mausoleums</option>
<option value="Museums & Collections">Museums & Collections</option>
<option value="Natural & Cultural Landscapes">Natural & Cultural Landscapes</option>
<option value="Monuments & Memorial Landscapes">Monuments & Memorial Landscapes</option>
</select>

<select id="period-filter">
<option value="">All Periods</option>
{% assign periods = site.data.fieldwork.sites | map: "period" | flatten | uniq | sort %}
{% for period in periods %}
<option value="{{ period }}">{{ period }}</option>
{% endfor %}
</select>

<select id="lens-filter">
<option value="">All Research Lenses</option>
{% for lens in site.data.fieldwork.research_lenses %}
<option value="{{ lens }}">{{ lens }}</option>
{% endfor %}
</select>

</div>

<div id="site-count">
Showing {{ site.data.fieldwork.sites | size }} sites
</div>

---

## Site Catalogue

{% for item in site.data.fieldwork.sites %}

<article class="heritage-site"
data-category="{{ item.category.primary }}"
data-period="{{ item.period | join: '|' }}"
data-lens="{{ item.research_lens | join: '|' }}">

<h3>{{ item.name_en }}</h3>

<p>{{ item.name_zh }}</p>

<p><strong>Location:</strong> {{ item.location.city }}, {{ item.location.province }}</p>

<p><strong>Period:</strong> {{ item.period | join: ", " }}</p>

<p><strong>Category:</strong> {{ item.category.primary }}</p>

<p><strong>Research Themes:</strong> {{ item.research_lens | join: " · " }}</p>

<div class="field-visit-placeholder">
<strong>Field Visit:</strong> To be added
</div>

<div class="field-photo-placeholder">
Field photograph to be added
</div>

</article>

{% endfor %}

<script>
document.addEventListener("DOMContentLoaded", function(){
  if(typeof L !== "undefined"){
    const map=L.map("heritage-map");
    L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png").addTo(map);

    let markers=[];

    {% for item in site.data.fieldwork.sites %}
    {% if item.location.latitude and item.location.longitude %}
    let marker{{forloop.index}}=L.circleMarker(
      [{{item.location.latitude}},{{item.location.longitude}}]
    ).addTo(map).bindPopup("{{item.name_en}}<br>{{item.name_zh}}");

    markers.push(marker{{forloop.index}});
    {% endif %}
    {% endfor %}

    if(markers.length){
      map.fitBounds(L.featureGroup(markers).getBounds());
    }
  }
});
</script>
