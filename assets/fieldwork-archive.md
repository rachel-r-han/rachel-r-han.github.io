---
layout: default
title: Fieldwork Archive
permalink: /fieldwork/
---

# Fieldwork Archive

> **76 sites · 8 research lenses · 5 field research cases**

This archive documents my fieldwork across historical sites, museums, memorial spaces, religious sites, architectural heritage, and cultural landscapes in China.

Rather than treating these places simply as destinations, I approach them as **field laboratories for public history**: spaces where historical narratives are selected, materialized, experienced, and emotionally interpreted.

## Research Framework

**Space → Narrative → Emotion**

The archive is organized through six primary site categories and eight recurring research lenses.

### Research Lenses

- Spatial Scale
- Emotional Distance
- Narrative Structure
- Material Proximity
- Historical Memory
- Memorialization
- Public History
- Heritage & Conservation

## Browse the Archive

<div class="fieldwork-filters">
  <label for="fieldwork-category">Category</label>
  <select id="fieldwork-category">
    <option value="">All categories</option>
    {% for category in site.data.fieldwork.categories %}
    <option value="{{ category }}">{{ category }}</option>
    {% endfor %}
  </select>

  <label for="fieldwork-period">Period</label>
  <select id="fieldwork-period">
    <option value="">All periods</option>
    {% assign periods = site.data.fieldwork.sites | map: "period" | flatten | uniq | sort %}
    {% for period in periods %}
    <option value="{{ period }}">{{ period }}</option>
    {% endfor %}
  </select>

  <label for="fieldwork-lens">Research Lens</label>
  <select id="fieldwork-lens">
    <option value="">All lenses</option>
    {% for lens in site.data.fieldwork.research_lenses %}
    <option value="{{ lens }}">{{ lens }}</option>
    {% endfor %}
  </select>
</div>

<div id="fieldwork-count" class="fieldwork-count">
  Showing {{ site.data.fieldwork.sites | size }} sites
</div>

<div class="fieldwork-grid" id="fieldwork-grid">
{% for item in site.data.fieldwork.sites %}
<article class="fieldwork-card"
  data-category="{{ item.category.primary | escape }}"
  data-period="{{ item.period | join: '|' | escape }}"
  data-lenses="{{ item.research_lens | join: '|' | escape }}">
  <div class="fieldwork-card__meta">
    {% if item.location.city %}<span>{{ item.location.city }}</span>{% endif %}
    {% if item.location.province %}<span>{{ item.location.province }}</span>{% endif %}
  </div>

  <h2>{{ item.name_en }}</h2>
  <p class="fieldwork-card__zh">{{ item.name_zh }}</p>
  <p class="fieldwork-card__category">{{ item.category.primary }}</p>

  <div class="fieldwork-card__lenses">
    {% for lens in item.research_lens %}
    <span class="research-tag">{{ lens }}</span>
    {% endfor %}
  </div>

  {% if item.field_research.years.size > 0 %}
  <p class="fieldwork-card__visited">Visited: {{ item.field_research.years | join: ", " }}</p>
  {% endif %}
</article>
{% endfor %}
</div>

<script>
document.addEventListener("DOMContentLoaded", function () {
  const category = document.getElementById("fieldwork-category");
  const period = document.getElementById("fieldwork-period");
  const lens = document.getElementById("fieldwork-lens");
  const cards = Array.from(document.querySelectorAll(".fieldwork-card"));
  const count = document.getElementById("fieldwork-count");

  function filterSites() {
    let visible = 0;
    cards.forEach(card => {
      const okCategory = !category.value || card.dataset.category === category.value;
      const okPeriod = !period.value || card.dataset.period.split("|").includes(period.value);
      const okLens = !lens.value || card.dataset.lenses.split("|").includes(lens.value);
      const show = okCategory && okPeriod && okLens;
      card.hidden = !show;
      if (show) visible++;
    });
    count.textContent = `Showing ${visible} site${visible === 1 ? "" : "s"}`;
  }

  [category, period, lens].forEach(select => select.addEventListener("change", filterSites));
});
</script>
