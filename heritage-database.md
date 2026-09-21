
---
title: "Heritage Database"
layout: single
permalink: /heritage-database/
toc: false
sidebar:
  nav: "fieldwork-categories"
---

<style>
/* -------------------------------------------------------
   Heritage Database V7
   Academic / restrained visual treatment
   ------------------------------------------------------- */

.archive-intro {
  margin-bottom: 2.2rem;
}

.archive-intro p {
  max-width: 760px;
  margin-bottom: 0;
}

.archive-stats {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 14px;
  margin: 2rem 0 3rem;
}

.archive-stat {
  border: 1px solid #e4e4e1;
  background: #fafaf8;
  padding: 1.25rem 1.4rem;
  min-height: 92px;
  display: flex;
  align-items: baseline;
  gap: 12px;
}

.archive-stat-number {
  font-size: 2.25rem;
  line-height: 1;
  font-weight: 600;
  color: #34383b;
}

.archive-stat-label {
  font-size: 0.92rem;
  color: #686d70;
  letter-spacing: 0.02em;
}

.map-section {
  margin-top: 1rem;
}

.map-header {
  margin-bottom: 1.2rem;
}

.map-header p {
  max-width: 760px;
  margin-bottom: 0;
}

#heritage-map {
  height: 600px;
  width: 100%;
  border: 1px solid #d9d9d5;
  background: #f4f3ef;
}

.map-legend {
  background: rgba(255,255,255,0.96);
  border: 1px solid #deded9;
  padding: 12px 15px;
  min-width: 220px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.08);
  font-size: 13px;
  line-height: 1.55;
}

.map-legend-title {
  font-weight: 600;
  margin-bottom: 7px;
  color: #3d4143;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 4px 0;
  color: #505457;
}

.legend-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  flex: 0 0 10px;
}

.map-note {
  margin-top: 0.9rem;
  color: #777b7d;
  font-size: 0.88rem;
}

.archive-browse {
  margin-top: 3.5rem;
}

.archive-filters {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 12px;
  margin: 1.5rem 0 1rem;
}

.archive-filter {
  border: 1px solid #deded9;
  background: #fff;
  padding: 0.8rem 0.95rem;
}

.archive-filter label {
  display: block;
  margin: 0;
}

.archive-filter-label {
  display: block;
  font-size: 0.78rem;
  color: #777b7d;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  margin-bottom: 0.35rem;
}

.archive-filter select {
  width: 100%;
  border: 0;
  background: transparent;
  padding: 0;
  font-size: 0.96rem;
  color: #404447;
}

.archive-actions {
  display: flex;
  justify-content: flex-end;
  margin-bottom: 1.2rem;
}

.archive-reset {
  border: 1px solid #9b9e9f;
  background: transparent;
  padding: 0.45rem 0.9rem;
  font-size: 0.84rem;
  color: #4e5254;
  cursor: pointer;
}

.archive-reset:hover {
  background: #f5f5f2;
}

#site-count {
  color: #6d7173;
  font-size: 0.9rem;
  margin: 0.8rem 0 1.8rem;
}

#site-catalogue {
  margin-top: 1rem;
}

.heritage-site {
  border-top: 1px solid #deded9;
  padding: 1.65rem 0 1.8rem;
}

.heritage-site:last-child {
  border-bottom: 1px solid #deded9;
}

.heritage-site h3 {
  margin-bottom: 0.35rem;
}

.site-category-tag {
  display: inline-block;
  margin: 0.3rem 0 0.8rem;
  padding: 0.2rem 0.55rem;
  border: 1px solid #d9d9d5;
  font-size: 0.76rem;
  color: #555a5c;
  background: #fafaf8;
}

.site-meta {
  margin: 0.35rem 0;
  color: #666b6d;
  font-size: 0.9rem;
}

@media (max-width: 800px) {
  .archive-stats,
  .archive-filters {
    grid-template-columns: 1fr;
  }

  #heritage-map {
    height: 480px;
  }
}
</style>

<div class="archive-intro">

This database documents historical and heritage sites visited across China through longitudinal field research.

</div>

<div class="archive-stats">

<div class="archive-stat">
<span class="archive-stat-number">75</span>
<span class="archive-stat-label">Documented Sites</span>
</div>

<div class="archive-stat">
<span class="archive-stat-number">4</span>
<span class="archive-stat-label">Site Categories</span>
</div>

<div class="archive-stat">
<span class="archive-stat-number">8</span>
<span class="archive-stat-label">Research Lenses</span>
</div>

</div>

---

## Interactive Map

<div class="map-header">

Explore the geographical distribution of my fieldwork sites across China.

</div>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<div id="heritage-map"></div>

<p class="map-note">
Map visualization based on 75 documented heritage sites in the fieldwork archive.
</p>

---

## Browse Archive

<div class="archive-browse">

Filter and explore sites by category, historical period, and research lens.

<div class="archive-filters">

<div class="archive-filter">
<label for="category-filter">
<span class="archive-filter-label">Category</span>
<select id="category-filter">
<option value="">All Categories</option>
<option value="Tombs & Mausoleums">Tombs & Mausoleums</option>
<option value="Museums & Collections">Museums & Collections</option>
<option value="Natural & Cultural Landscapes">Natural & Cultural Landscapes</option>
<option value="Monuments & Memorial Landscapes">Monuments & Memorial Landscapes</option>
</select>
</label>
</div>

<div class="archive-filter">
<label for="period-filter">
<span class="archive-filter-label">Historical Period</span>
<select id="period-filter">
<option value="">All Periods</option>
{% assign periods = site.data.fieldwork.sites | map: "period" | flatten | uniq | sort %}
{% for period in periods %}
<option value="{{ period }}">{{ period }}</option>
{% endfor %}
</select>
</label>
</div>

<div class="archive-filter">
<label for="lens-filter">
<span class="archive-filter-label">Research Lens</span>
<select id="lens-filter">
<option value="">All Research Lenses</option>
{% for lens in site.data.fieldwork.research_lenses %}
<option value="{{ lens }}">{{ lens }}</option>
{% endfor %}
</select>
</label>
</div>

</div>

<div class="archive-actions">
<button type="button" class="archive-reset" id="archive-reset">Reset Filters</button>
</div>

<div id="site-count">
Showing {{ site.data.fieldwork.sites | size }} sites
</div>

</div>

---

## Site Catalogue

Each entry is structured to accommodate future fieldwork documentation. The current database remains unchanged; the catalogue simply reserves space for a visit date and a field photograph. When those fields are later added to `_data/fieldwork.yml`, the card can display them without changing the overall page structure.

<style>
/* -------------------------------------------------------
   Site Catalogue V8
   Academic fieldwork entry cards
   Reserved fields: visit date + field photograph
   ------------------------------------------------------- */

#site-catalogue {
  margin-top: 1rem;
}

.heritage-site {
  border-top: 1px solid #deded9;
  padding: 1.7rem 0;
}

.heritage-site:last-child {
  border-bottom: 1px solid #deded9;
}

.site-card {
  display: grid;
  grid-template-columns: minmax(0, 1fr) 210px;
  gap: 2rem;
  align-items: start;
}

.site-card-content {
  min-width: 0;
}

.site-card-title {
  margin: 0 0 0.2rem;
  font-size: 1.35rem;
  line-height: 1.3;
}

.site-card-name-zh {
  margin: 0 0 0.85rem;
  color: #5e6365;
  font-size: 1rem;
}

.site-category-tag {
  display: inline-block;
  margin: 0 0 1rem;
  padding: 0.22rem 0.58rem;
  border: 1px solid #d9d9d5;
  background: #fafaf8;
  color: #555a5c;
  font-size: 0.75rem;
  letter-spacing: 0.02em;
}

.site-meta-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 0.55rem 1.5rem;
  margin: 0;
}

.site-meta {
  margin: 0;
  color: #666b6d;
  font-size: 0.88rem;
  line-height: 1.55;
}

.site-meta strong {
  color: #4d5254;
  font-weight: 600;
}

.site-themes {
  margin-top: 0.9rem;
  padding-top: 0.8rem;
  border-top: 1px solid #eeeeeb;
}

.site-themes-label {
  display: block;
  margin-bottom: 0.25rem;
  color: #777b7d;
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}

.site-themes-text {
  margin: 0;
  color: #626769;
  font-size: 0.88rem;
  line-height: 1.55;
}

/* Future field photograph area.
   No database change is required now.
   When item.field_photo is later added, the image will
   automatically replace the placeholder. */

.site-photo-slot {
  width: 100%;
  aspect-ratio: 4 / 3;
  border: 1px solid #deded9;
  background: #f7f7f4;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  overflow: hidden;
}

.site-photo-slot img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.site-photo-placeholder {
  padding: 1rem;
  color: #999d9e;
  font-size: 0.76rem;
  line-height: 1.5;
  letter-spacing: 0.02em;
}

.site-visit-placeholder {
  margin-top: 0.75rem;
  padding-top: 0.7rem;
  border-top: 1px solid #eeeeeb;
  color: #85898a;
  font-size: 0.82rem;
}

.site-visit-placeholder strong {
  color: #656a6c;
  font-weight: 600;
}

@media (max-width: 700px) {
  .site-card {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .site-photo-slot {
    max-width: 280px;
  }

  .site-meta-grid {
    grid-template-columns: 1fr;
  }
}
</style>

<div id="site-catalogue">

{% for item in site.data.fieldwork.sites %}

<article class="heritage-site"
data-category="{{ item.category.primary }}"
data-period="{{ item.period | join: '|' }}"
data-lens="{{ item.research_lens | join: '|' }}">

<div class="site-card">

<div class="site-card-content">

<h3 class="site-card-title">{{ item.name_en }}</h3>

<p class="site-card-name-zh">{{ item.name_zh }}</p>

<span class="site-category-tag">{{ item.category.primary }}</span>

<div class="site-meta-grid">

<p class="site-meta">
<strong>Location:</strong>
{{ item.location.city }}, {{ item.location.province }}
</p>

<p class="site-meta">
<strong>Period:</strong>
{{ item.period | join: ", " }}
</p>

</div>

<div class="site-themes">

<span class="site-themes-label">Research Themes</span>

<p class="site-themes-text">
{{ item.research_lens | join: " · " }}
</p>

</div>

<div class="site-visit-placeholder">

<strong>Field Visit:</strong>
{% if item.visit_date %}
{{ item.visit_date }}
{% else %}
Visit date to be added
{% endif %}

</div>

</div>

<div class="site-photo-slot">

{% if item.field_photo %}
<img src="{{ item.field_photo | relative_url }}"
alt="Field photograph of {{ item.name_en }}">
{% else %}
<div class="site-photo-placeholder">
Field photograph<br>
to be added
</div>
{% endif %}

</div>

</div>

</article>

{% endfor %}

</div>

<script>
document.addEventListener("DOMContentLoaded", function () {

  /* ---------------------------
     Leaflet map
     --------------------------- */

  if (typeof L !== "undefined") {

    const map = L.map("heritage-map", {
      scrollWheelZoom: false
    });

    L.tileLayer(
      "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      {
        attribution: "&copy; OpenStreetMap contributors",
        maxZoom: 18
      }
    ).addTo(map);

    const categoryColors = {
      "Tombs & Mausoleums": "#a95c5c",
      "Museums & Collections": "#477aa6",
      "Natural & Cultural Landscapes": "#5f866e",
      "Monuments & Memorial Landscapes": "#c28a43"
    };

    const categoryCounts = {
      "Tombs & Mausoleums": 0,
      "Museums & Collections": 0,
      "Natural & Cultural Landscapes": 0,
      "Monuments & Memorial Landscapes": 0
    };

    const markers = [];

    {% for item in site.data.fieldwork.sites %}
    {% if item.location.latitude and item.location.longitude %}

    const category{{ forloop.index }} = {{ item.category.primary | jsonify }};
    const color{{ forloop.index }} =
      categoryColors[category{{ forloop.index }}] || "#6b7072";

    categoryCounts[category{{ forloop.index }}]++;

    const marker{{ forloop.index }} = L.circleMarker(
      [
        {{ item.location.latitude }},
        {{ item.location.longitude }}
      ],
      {
        radius: 7,
        color: color{{ forloop.index }},
        weight: 1.5,
        fillColor: color{{ forloop.index }},
        fillOpacity: 0.82
      }
    )
    .addTo(map)
    .bindPopup(`
      <div style="min-width:190px;">
        <strong>{{ item.name_en }}</strong><br>
        {{ item.name_zh }}<br><br>
        <span><strong>Location:</strong> {{ item.location.city }}, {{ item.location.province }}</span><br>
        <span><strong>Category:</strong> {{ item.category.primary }}</span><br>
        <span><strong>Period:</strong> {{ item.period | join: ", " }}</span>
      </div>
    `);

    markers.push(marker{{ forloop.index }});

    {% endif %}
    {% endfor %}

    if (markers.length > 0) {
      const group = L.featureGroup(markers);

      map.fitBounds(
        group.getBounds(),
        {
          padding: [45, 45]
        }
      );
    } else {
      map.setView([35.8, 104.1], 4);
    }

    /* Four-category academic legend */

    const legend = L.control({ position: "topright" });

    legend.onAdd = function () {

      const div = L.DomUtil.create("div", "map-legend");

      div.innerHTML = `
        <div class="map-legend-title">Site Categories</div>
        <div class="legend-item">
          <span class="legend-dot" style="background:${categoryColors["Tombs & Mausoleums"]}"></span>
          <span>Tombs & Mausoleums (<span id="legend-tombs">0</span>)</span>
        </div>
        <div class="legend-item">
          <span class="legend-dot" style="background:${categoryColors["Museums & Collections"]}"></span>
          <span>Museums & Collections (<span id="legend-museums">0</span>)</span>
        </div>
        <div class="legend-item">
          <span class="legend-dot" style="background:${categoryColors["Natural & Cultural Landscapes"]}"></span>
          <span>Natural & Cultural Landscapes (<span id="legend-natural">0</span>)</span>
        </div>
        <div class="legend-item">
          <span class="legend-dot" style="background:${categoryColors["Monuments & Memorial Landscapes"]}"></span>
          <span>Monuments & Memorial Landscapes (<span id="legend-monuments">0</span>)</span>
        </div>
      `;

      L.DomEvent.disableClickPropagation(div);

      return div;
    };

    legend.addTo(map);

    document.getElementById("legend-tombs").textContent =
      categoryCounts["Tombs & Mausoleums"];

    document.getElementById("legend-museums").textContent =
      categoryCounts["Museums & Collections"];

    document.getElementById("legend-natural").textContent =
      categoryCounts["Natural & Cultural Landscapes"];

    document.getElementById("legend-monuments").textContent =
      categoryCounts["Monuments & Memorial Landscapes"];

  }

  /* ---------------------------
     Archive filters
     --------------------------- */

  const categoryFilter = document.getElementById("category-filter");
  const periodFilter = document.getElementById("period-filter");
  const lensFilter = document.getElementById("lens-filter");
  const resetButton = document.getElementById("archive-reset");
  const siteCount = document.getElementById("site-count");
  const sites = Array.from(
    document.querySelectorAll("#site-catalogue .heritage-site")
  );

  function updateArchive() {

    const category = categoryFilter.value;
    const period = periodFilter.value;
    const lens = lensFilter.value;

    let visible = 0;

    sites.forEach(function (site) {

      const siteCategory = site.dataset.category || "";
      const sitePeriods = (site.dataset.period || "").split("|");
      const siteLenses = (site.dataset.lens || "").split("|");

      const categoryMatch =
        !category || siteCategory === category;

      const periodMatch =
        !period || sitePeriods.includes(period);

      const lensMatch =
        !lens || siteLenses.includes(lens);

      const show =
        categoryMatch &&
        periodMatch &&
        lensMatch;

      site.style.display = show ? "" : "none";

      if (show) {
        visible++;
      }
    });

    siteCount.textContent =
      "Showing " + visible + " of " + sites.length + " sites";
  }

  categoryFilter.addEventListener("change", updateArchive);
  periodFilter.addEventListener("change", updateArchive);
  lensFilter.addEventListener("change", updateArchive);

  resetButton.addEventListener("click", function () {
    categoryFilter.value = "";
    periodFilter.value = "";
    lensFilter.value = "";
    updateArchive();
  });

});
</script>
