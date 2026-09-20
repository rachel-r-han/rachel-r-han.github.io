---
layout: single
permalink: /heritage-database/
sidebar:
  nav: fieldwork-categories
title: Heritage Database
toc: false
---

## Archive Overview

This database documents historical and heritage sites visited across
China through longitudinal field research.

::: archive-overview
::: overview-item
`<strong>`{=html}75`</strong>`{=html} Documented Sites
:::

::: overview-item
`<strong>`{=html}6`</strong>`{=html} Site Categories
:::

::: overview-item
`<strong>`{=html}8`</strong>`{=html} Research Lenses
:::
:::

------------------------------------------------------------------------

## Interactive Map

Explore the geographical distribution of my fieldwork sites across
China.

::: {#heritage-map style="height:600px;width:100%;"}
:::

```{=html}
<p class="map-note">
```
Map visualization based on documented heritage sites in the fieldwork
archive.
```{=html}
</p>
```

------------------------------------------------------------------------

## Browse Archive

Filter documented sites by category, historical period, and research
lens.

::: archive-filters
`<label>`{=html} Category `<select id="category-filter">`{=html}
`<option value="">`{=html}All Categories`</option>`{=html} {% for
category in site.data.fieldwork.categories %}
`<option value="{{ category }}">`{=html}{{ category }}`</option>`{=html}
{% endfor %} `</select>`{=html} `</label>`{=html}

`<label>`{=html} Period `<select id="period-filter">`{=html}
`<option value="">`{=html}All Periods`</option>`{=html} {% assign
periods = site.data.fieldwork.sites \| map: "period" \| flatten \| uniq
\| sort %} {% for period in periods %}
`<option value="{{ period }}">`{=html}{{ period }}`</option>`{=html} {%
endfor %} `</select>`{=html} `</label>`{=html}

`<label>`{=html} Research Lens `<select id="lens-filter">`{=html}
`<option value="">`{=html}All Research Lenses`</option>`{=html} {% for
lens in site.data.fieldwork.research_lenses %}
`<option value="{{ lens }}">`{=html}{{ lens }}`</option>`{=html} {%
endfor %} `</select>`{=html} `</label>`{=html}
:::

::: {#site-count}
Showing {{ site.data.fieldwork.sites \| size }} sites
:::

------------------------------------------------------------------------

## Site Catalogue

::: {#site-catalogue}
{% for item in site.data.fieldwork.sites %}

```{=html}
<article class="heritage-site" data-category="{{ item.category.primary }}" data-period="{{ item.period | join: &#39;|&#39; }}" data-lens="{{ item.research_lens | join: &#39;|&#39; }}">
```
```{=html}
<h3>
```
{{ item.name_en }}
```{=html}
</h3>
```
```{=html}
<p>
```
{{ item.name_zh }}
```{=html}
</p>
```
```{=html}
<p>
```
`<strong>`{=html}Location:`</strong>`{=html} {{ item.location.city }},
{{ item.location.province }}
```{=html}
</p>
```
```{=html}
<p>
```
`<strong>`{=html}Category:`</strong>`{=html} {{ item.category.primary }}
```{=html}
</p>
```
```{=html}
<p>
```
`<strong>`{=html}Period:`</strong>`{=html} {{ item.period \| join: ","
}}
```{=html}
</p>
```
```{=html}
<p>
```
`<strong>`{=html}Research Themes:`</strong>`{=html} {{
item.research_lens \| join: " · " }}
```{=html}
</p>
```
```{=html}
</article>
```
{% endfor %}
:::

```{=html}
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

let marker{{forloop.index}} = L.marker([
{{item.location.latitude}},
{{item.location.longitude}}
])
.addTo(map)
.bindPopup(
"<strong>{{item.name_en}}</strong><br>{{item.name_zh}}<br>{{item.location.city}}, {{item.location.province}}"
);

markers.push(marker{{forloop.index}});

{% endif %}
{% endfor %}

if(markers.length){
map.fitBounds(
L.featureGroup(markers).getBounds(),
{padding:[40,40]}
);
}

});

</script>
```
