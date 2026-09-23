---
title: "Heritage Database"
layout: single
permalink: /heritage-database/
toc: false
sidebar:
  nav: "fieldwork-categories"
---

<style>
/* ===========================================================
   Heritage Database — Visual Refinement V2
   - No font-family override (keeps site typography unified)
   - Statistics cards: neutral academic palette
   - Fixed overflow inside stat cards
   =========================================================== */

:root {
  --hd-ink:        #26292c;
  --hd-ink-soft:   #56595c;
  --hd-muted:      #767a7d;
  --hd-line:       #e4e3de;
  --hd-line-soft:  #eeeeea;
  --hd-paper:      #fbfaf7;

  /* category palette (unchanged) */
  --cat-tomb-bg:      #fbe9e6;
  --cat-tomb-fg:      #a84a41;
  --cat-museum-bg:    #e4eef9;
  --cat-museum-fg:    #3b6ba3;
  --cat-natural-bg:   #e5f1e8;
  --cat-natural-fg:   #3e7350;
  --cat-monument-bg:  #faf0d9;
  --cat-monument-fg:  #966a1e;
}

/* -----------------------------------------------------------
   1 · Layout width
   ----------------------------------------------------------- */

.initial-content,
.page {
  max-width: 1600px;
}

.page__inner-wrap {
  max-width: 1480px;
}

.page__content {
  max-width: 1280px;
  width: 100%;
}

@media (max-width: 800px) {
  .page__content { max-width: 100%; }
}

/* -----------------------------------------------------------
   2 · Headings — keep site default font, only refine spacing
   ----------------------------------------------------------- */

.page__title {
  font-weight: 600;
  font-size: clamp(1.9rem, 3.2vw, 2.5rem);
  letter-spacing: -0.012em;
  color: var(--hd-ink);
  margin: 0 0 0.45rem;
  line-height: 1.18;
}

.page__content h2 {
  font-weight: 600;
  font-size: 1.4rem;
  letter-spacing: -0.005em;
  color: var(--hd-ink);
  margin-top: 3rem;
  margin-bottom: 0.65rem;
  position: relative;
  display: inline-block;
}

.page__content h2::after {
  content: "";
  display: inline-block;
  width: 40px;
  height: 1px;
  background: var(--hd-ink);
  margin-left: 16px;
  vertical-align: 6px;
  opacity: 0.5;
}

/* -----------------------------------------------------------
   3 · Intro subtitle
   ----------------------------------------------------------- */

.archive-intro {
  margin-bottom: 0;
}

.archive-intro p {
  max-width: 720px;
  margin-bottom: 0;
  font-size: 1.02rem;
  color: var(--hd-ink-soft);
  font-style: italic;
  letter-spacing: 0.005em;
  line-height: 1.55;
}

/* -----------------------------------------------------------
   4 · Statistics — neutral academic cards, overflow fixed
   ----------------------------------------------------------- */

.archive-stats {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 14px;
  margin: 2.2rem 0 3.2rem;
}

.archive-stat {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 1rem 1.1rem;
  border: 1px solid var(--hd-line);
  border-radius: 6px;
  background: #fff;
  min-height: 88px;
  min-width: 0;                     /* critical: allows flex child to shrink */
  transition: border-color 0.18s ease, box-shadow 0.18s ease;
}

.archive-stat:hover {
  border-color: #c9c8c2;
  box-shadow: 0 4px 12px rgba(40, 40, 40, 0.05);
}

.archive-stat-icon {
  width: 36px;
  height: 36px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  background: #f5f4f0;
  border: 1px solid var(--hd-line);
  color: var(--hd-ink-soft);
}

.archive-stat-icon svg {
  width: 18px;
  height: 18px;
  stroke-width: 1.8;
  fill: none;
}

.archive-stat-body {
  display: flex;
  flex-direction: column;
  gap: 2px;
  min-width: 0;                     /* critical: allows text to wrap/shrink */
  flex: 1;
}

.archive-stat-number {
  font-size: clamp(1.15rem, 1.5vw, 1.45rem);
  font-weight: 600;
  line-height: 1.1;
  color: var(--hd-ink);
  letter-spacing: -0.01em;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.archive-stat-label {
  font-size: 0.78rem;
  color: var(--hd-muted);
  line-height: 1.3;
  letter-spacing: 0.01em;
  overflow-wrap: anywhere;
}

/* -----------------------------------------------------------
   5 · Map
   ----------------------------------------------------------- */

.map-section {
  margin-top: 1rem;
}

.map-header {
  margin-bottom: 1.2rem;
}

.map-header p {
  max-width: 760px;
  margin-bottom: 0;
  color: var(--hd-ink-soft);
  font-size: 0.98rem;
}

#heritage-map {
  height: 560px;
  width: 100%;
  border: 1px solid var(--hd-line);
  border-radius: 6px;
  background: #f4f3ef;
  overflow: hidden;
}

.leaflet-container {
  border-radius: 6px;
  font-family: inherit;
}

.map-legend {
  background: rgba(255, 255, 255, 0.97);
  border: 1px solid var(--hd-line);
  border-radius: 6px;
  padding: 13px 16px;
  min-width: 230px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
  font-size: 13px;
  line-height: 1.55;
}

.map-legend-title {
  font-weight: 600;
  margin-bottom: 8px;
  color: var(--hd-ink);
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 5px 0;
  color: var(--hd-ink-soft);
}

.legend-dot {
  width: 9px;
  height: 9px;
  border-radius: 50%;
  flex: 0 0 9px;
}

.map-note {
  margin-top: 0.9rem;
  color: #8b8e8f;
  font-size: 0.85rem;
}

/* -----------------------------------------------------------
   6 · Browse archive — filters
   ----------------------------------------------------------- */

.archive-browse {
  margin-top: 3.2rem;
}

.archive-filters {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 14px;
  margin: 1.5rem 0 1rem;
}

.archive-filter {
  position: relative;
  border: 1px solid var(--hd-line);
  border-radius: 6px;
  background: #fff;
  padding: 0.72rem 2.6rem 0.72rem 3.2rem;
  transition: border-color 0.15s ease;
}

.archive-filter:hover {
  border-color: #c9c8c2;
}

.archive-filter::before {
  content: "";
  position: absolute;
  left: 1.05rem;
  top: 50%;
  transform: translateY(-50%);
  width: 20px;
  height: 20px;
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
  opacity: 0.55;
}

.archive-filter:nth-child(1)::before {
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23767a7d' stroke-width='1.8' stroke-linecap='round' stroke-linejoin='round'><polygon points='12 2 2 7 12 12 22 7 12 2'/><polyline points='2 17 12 22 22 17'/><polyline points='2 12 12 17 22 12'/></svg>");
}

.archive-filter:nth-child(2)::before {
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23767a7d' stroke-width='1.8' stroke-linecap='round' stroke-linejoin='round'><rect x='3' y='4' width='18' height='18' rx='2'/><line x1='16' y1='2' x2='16' y2='6'/><line x1='8' y1='2' x2='8' y2='6'/><line x1='3' y1='10' x2='21' y2='10'/></svg>");
}

.archive-filter:nth-child(3)::before {
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23767a7d' stroke-width='1.8' stroke-linecap='round' stroke-linejoin='round'><path d='M20.59 13.41l-7.17 7.17a2 2 0 0 1-2.83 0L2 12V2h10l8.59 8.59a2 2 0 0 1 0 2.82z'/><line x1='7' y1='7' x2='7.01' y2='7'/></svg>");
}

.archive-filter::after {
  content: "";
  position: absolute;
  right: 1.1rem;
  top: 50%;
  width: 7px;
  height: 7px;
  border-right: 1.6px solid #9b9d9e;
  border-bottom: 1.6px solid #9b9d9e;
  transform: translateY(-70%) rotate(45deg);
  pointer-events: none;
}

.archive-filter label {
  display: block;
  margin: 0;
}

.archive-filter-label {
  display: block;
  font-size: 0.68rem;
  color: var(--hd-muted);
  text-transform: uppercase;
  letter-spacing: 0.09em;
  margin-bottom: 0.15rem;
  font-weight: 600;
}

.archive-filter select {
  width: 100%;
  border: 0;
  background: transparent;
  padding: 0;
  font-size: 0.94rem;
  color: var(--hd-ink);
  font-weight: 500;
  cursor: pointer;
  appearance: none;
  -webkit-appearance: none;
  outline: none;
  font-family: inherit;
}

.archive-actions {
  display: flex;
  justify-content: flex-end;
  margin-bottom: 1.1rem;
}

.archive-reset {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  border: 1px solid var(--hd-line);
  border-radius: 6px;
  background: #fff;
  padding: 0.5rem 1rem;
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--hd-ink-soft);
  cursor: pointer;
  transition: all 0.15s ease;
  font-family: inherit;
}

.archive-reset::before {
  content: "↻";
  font-size: 1rem;
  line-height: 1;
  color: var(--hd-muted);
}

.archive-reset:hover {
  background: #f5f4f0;
  border-color: #c9c8c2;
  color: var(--hd-ink);
}

#site-count {
  color: var(--hd-muted);
  font-size: 0.88rem;
  margin: 0.8rem 0 1.8rem;
  letter-spacing: 0.01em;
}

/* -----------------------------------------------------------
   7 · Site catalogue — card grid
   ----------------------------------------------------------- */

#site-catalogue {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(255px, 1fr));
  gap: 22px;
  margin-top: 1.8rem;
}

.heritage-site {
  border: none;
  padding: 0;
  margin: 0;
}

.site-card {
  display: flex;
  flex-direction: column;
  height: 100%;
  border: 1px solid var(--hd-line);
  border-radius: 8px;
  background: #fff;
  overflow: hidden;
  transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease;
}

.site-card:hover {
  border-color: #cfcec8;
  box-shadow: 0 8px 24px rgba(40, 40, 40, 0.08);
  transform: translateY(-2px);
}

.site-photo-slot {
  order: 1;
  width: 100%;
  aspect-ratio: 4 / 3;
  border: none;
  border-bottom: 1px solid var(--hd-line-soft);
  background: linear-gradient(135deg, #f2efe9 0%, #e7e4dc 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  flex-shrink: 0;
}

.site-photo-slot img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.4s ease;
}

.site-card:hover .site-photo-slot img {
  transform: scale(1.03);
}

.site-photo-placeholder {
  padding: 1rem;
  color: #a8a8a2;
  font-size: 0.74rem;
  line-height: 1.55;
  letter-spacing: 0.03em;
  text-align: center;
}

.site-card-content {
  order: 2;
  padding: 1.05rem 1.15rem 1.2rem;
  display: flex;
  flex-direction: column;
  flex: 1;
  min-width: 0;
}

.site-category-tag {
  display: inline-block;
  align-self: flex-start;
  margin: 0 0 0.75rem;
  padding: 0.24rem 0.62rem;
  border: none;
  border-radius: 999px;
  font-size: 0.68rem;
  font-weight: 600;
  letter-spacing: 0.02em;
  background: #f0f0ec;
  color: #666;
}

.heritage-site[data-category="Tombs & Mausoleums"] .site-category-tag {
  background: var(--cat-tomb-bg);
  color: var(--cat-tomb-fg);
}
.heritage-site[data-category="Museums & Collections"] .site-category-tag {
  background: var(--cat-museum-bg);
  color: var(--cat-museum-fg);
}
.heritage-site[data-category="Natural & Cultural Landscapes"] .site-category-tag {
  background: var(--cat-natural-bg);
  color: var(--cat-natural-fg);
}
.heritage-site[data-category="Monuments & Memorial Landscapes"] .site-category-tag {
  background: var(--cat-monument-bg);
  color: var(--cat-monument-fg);
}

.site-card-title,
.site-card h3 {
  font-size: 1.08rem;
  font-weight: 600;
  line-height: 1.32;
  margin: 0 0 0.28rem;
  color: var(--hd-ink);
  letter-spacing: -0.005em;
}

.site-card-name-zh {
  margin: 0 0 0.85rem;
  font-size: 0.86rem;
  color: var(--hd-muted);
  letter-spacing: 0.03em;
}

.site-meta-grid {
  display: flex;
  flex-direction: column;
  gap: 0.38rem;
  margin-top: auto;
  padding-top: 0.75rem;
  border-top: 1px solid var(--hd-line-soft);
}

.site-meta {
  margin: 0;
  font-size: 0.82rem;
  color: var(--hd-ink-soft);
  line-height: 1.4;
  display: flex;
  align-items: center;
  gap: 7px;
}

.site-meta strong {
  display: none;
}

.site-meta-grid .site-meta:nth-child(1)::before {
  content: "";
  display: inline-block;
  width: 13px;
  height: 13px;
  flex-shrink: 0;
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23767a7d' stroke-width='1.9' stroke-linecap='round' stroke-linejoin='round'><path d='M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z'/><circle cx='12' cy='10' r='3'/></svg>");
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

.site-meta-grid .site-meta:nth-child(2)::before {
  content: "";
  display: inline-block;
  width: 13px;
  height: 13px;
  flex-shrink: 0;
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23767a7d' stroke-width='1.9' stroke-linecap='round' stroke-linejoin='round'><rect x='3' y='4' width='18' height='18' rx='2'/><line x1='16' y1='2' x2='16' y2='6'/><line x1='8' y1='2' x2='8' y2='6'/><line x1='3' y1='10' x2='21' y2='10'/></svg>");
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

.site-visit-placeholder {
  margin-top: 0.6rem;
  padding-top: 0.6rem;
  border-top: 1px dashed var(--hd-line-soft);
  font-size: 0.73rem;
  color: #a0a3a4;
  letter-spacing: 0.02em;
  line-height: 1.4;
}

.site-visit-placeholder strong {
  color: #8b8e8f;
  font-weight: 600;
  text-transform: uppercase;
  font-size: 0.66rem;
  letter-spacing: 0.07em;
  margin-right: 4px;
}

/* -----------------------------------------------------------
   8 · Responsive
   ----------------------------------------------------------- */

@media (max-width: 1100px) {
  .archive-stats {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 960px) {
  .archive-filters {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 600px) {
  .archive-stats {
    grid-template-columns: 1fr;
  }
  #site-catalogue {
    grid-template-columns: 1fr;
  }
  #heritage-map {
    height: 460px;
  }
  .page__content h2::after {
    display: none;
  }
}
</style>

<!-- =========================================================
     Intro
     ========================================================= -->

<div class="archive-intro">
  <p>
    A fieldwork archive of historical and heritage sites visited across China
    through longitudinal field research.
  </p>
</div>

<!-- =========================================================
     Statistics
     ========================================================= -->

{% assign sites_with_coords = 0 %}
{% for item in site.data.fieldwork.sites %}
  {% if item.location.latitude and item.location.longitude %}
    {% assign sites_with_coords = sites_with_coords | plus: 1 %}
  {% endif %}
{% endfor %}

<div class="archive-stats">

  <div class="archive-stat">
    <div class="archive-stat-icon" aria-hidden="true">
      <svg viewBox="0 0 24 24" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round">
        <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/>
        <circle cx="12" cy="10" r="3"/>
      </svg>
    </div>
    <div class="archive-stat-body">
      <span class="archive-stat-number">75</span>
      <span class="archive-stat-label">Documented Sites</span>
    </div>
  </div>

  <div class="archive-stat">
    <div class="archive-stat-icon" aria-hidden="true">
      <svg viewBox="0 0 24 24" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round">
        <polygon points="12 2 2 7 12 12 22 7 12 2"/>
        <polyline points="2 17 12 22 22 17"/>
        <polyline points="2 12 12 17 22 12"/>
      </svg>
    </div>
    <div class="archive-stat-body">
      <span class="archive-stat-number">4</span>
      <span class="archive-stat-label">Site Categories</span>
    </div>
  </div>

  <div class="archive-stat">
    <div class="archive-stat-icon" aria-hidden="true">
      <svg viewBox="0 0 24 24" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round">
        <path d="M4 4h10a3 3 0 0 1 3 3v13H7a3 3 0 0 1-3-3V4z"/>
        <path d="M17 7h3v13a3 3 0 0 1-3 3"/>
        <line x1="8" y1="9" x2="13" y2="9"/>
        <line x1="8" y1="13" x2="13" y2="13"/>
      </svg>
    </div>
    <div class="archive-stat-body">
      <span class="archive-stat-number">8</span>
      <span class="archive-stat-label">Research Lenses</span>
    </div>
  </div>

  <div class="archive-stat">
    <div class="archive-stat-icon" aria-hidden="true">
      <svg viewBox="0 0 24 24" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round">
        <polygon points="1 6 8 3 16 6 23 3 23 18 16 21 8 18 1 21 1 6"/>
        <line x1="8" y1="3" x2="8" y2="18"/>
        <line x1="16" y1="6" x2="16" y2="21"/>
      </svg>
    </div>
    <div class="archive-stat-body">
      <span class="archive-stat-number">{{ sites_with_coords }} / {{ site.data.fieldwork.sites | size }}</span>
      <span class="archive-stat-label">Sites with Coordinates</span>
    </div>
  </div>

</div>

---

## Interactive Map

<div class="map-header">
  <p>Explore the geographical distribution of my fieldwork sites across China.</p>
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

  <p style="color:#767a7d;font-size:0.96rem;margin-bottom:0;">
    Filter and explore sites by province, category, and historical period.
  </p>

  <div class="archive-filters">

    <div class="archive-filter">
      <label for="province-filter">
        <span class="archive-filter-label">Province</span>
        <select id="province-filter">
          <option value="">All Provinces</option>
          {% assign provinces = site.data.fieldwork.sites | map: "location" | map: "province" | uniq | sort %}
          {% for province in provinces %}
          <option value="{{ province }}">{{ province }}</option>
          {% endfor %}
        </select>
      </label>
    </div>

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

  </div>

  <div class="archive-actions">
    <button type="button" class="archive-reset" id="archive-reset">Reset Filters</button>
  </div>

  <div id="site-count">
    Showing {{ site.data.fieldwork.sites | size }} sites
  </div>

</div>

---

## Site Catalogue ({{ site.data.fieldwork.sites | size }})

<div id="site-catalogue">

{% for item in site.data.fieldwork.sites %}

<article class="heritage-site"
data-province="{{ item.location.province }}"
data-category="{{ item.category.primary }}"
data-period="{{ item.period | join: '|' }}"
data-lens="{{ item.research_lens | join: '|' }}">

<div class="site-card">

  <div class="site-photo-slot">
    {% if item.field_photo %}
    <img src="{{ item.field_photo | relative_url }}"
         alt="Field photograph of {{ item.name_en }}">
    {% else %}
    <div class="site-photo-placeholder">
      Field photograph<br>to be added
    </div>
    {% endif %}
  </div>

  <div class="site-card-content">

    <span class="site-category-tag">{{ item.category.primary }}</span>

    <h3 class="site-card-title">{{ item.name_en }}</h3>

    <p class="site-card-name-zh">{{ item.name_zh }}</p>

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

    <div class="site-visit-placeholder">
      <strong>Field Visit:</strong>
      {% if item.visit_date %}
      {{ item.visit_date }}
      {% else %}
      Visit date to be added
      {% endif %}
    </div>

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
      scrollWheelZoom: true
    });

    L.tileLayer(
      "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      {
        attribution: "&copy; OpenStreetMap contributors",
        maxZoom: 18
      }
    ).addTo(map);

    const categoryColors = {
      "Tombs & Mausoleums": "#b8615c",
      "Museums & Collections": "#4a7ab5",
      "Natural & Cultural Landscapes": "#5a8b6f",
      "Monuments & Memorial Landscapes": "#c48a3f"
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
        fillOpacity: 0.85
      }
    )
    .addTo(map)
    .bindPopup(`
      <div style="min-width:190px;font-family:inherit;">
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

    /* Legend */

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

  const provinceFilter = document.getElementById("province-filter");
  const categoryFilter = document.getElementById("category-filter");
  const periodFilter = document.getElementById("period-filter");
  const resetButton = document.getElementById("archive-reset");
  const siteCount = document.getElementById("site-count");
  const sites = Array.from(
    document.querySelectorAll("#site-catalogue .heritage-site")
  );

  function updateArchive() {

    const province = provinceFilter.value;
    const category = categoryFilter.value;
    const period = periodFilter.value;

    let visible = 0;

    sites.forEach(function (site) {

      const siteProvince = site.dataset.province || "";
      const siteCategory = site.dataset.category || "";
      const sitePeriods = (site.dataset.period || "").split("|");

      const provinceMatch =
        !province || siteProvince === province;

      const categoryMatch =
        !category || siteCategory === category;

      const periodMatch =
        !period || sitePeriods.includes(period);

      const show =
        provinceMatch &&
        categoryMatch &&
        periodMatch;

      site.style.display = show ? "" : "none";

      if (show) {
        visible++;
      }
    });

    siteCount.textContent =
      "Showing " + visible + " of " + sites.length + " sites";
  }

  provinceFilter.addEventListener("change", updateArchive);
  categoryFilter.addEventListener("change", updateArchive);
  periodFilter.addEventListener("change", updateArchive);

  resetButton.addEventListener("click", function () {
    provinceFilter.value = "";
    categoryFilter.value = "";
    periodFilter.value = "";
    updateArchive();
  });

});
</script>
