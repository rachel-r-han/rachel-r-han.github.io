---
layout: single
title: "Fieldwork Archive"
permalink: /fieldwork/
toc: false
---


# Fieldwork Archive


## 75 Heritage Sites Across China


This archive documents my longitudinal fieldwork across historical sites, museums, memorial spaces, religious sites, architectural heritage, and cultural landscapes in China.


Rather than treating these places simply as destinations, I approach them as **field laboratories for public history**: spaces where historical narratives are constructed, materialized, experienced, and emotionally interpreted.



<div style="
display:grid;
grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
gap:25px;
margin:40px 0;
">


<div>
<h2>75</h2>
<p>Heritage Sites</p>
</div>


<div>
<h2>20+</h2>
<p>Cities Across China</p>
</div>


<div>
<h2>8</h2>
<p>Research Lenses</p>
</div>


<div>
<h2>5</h2>
<p>Field Research Themes</p>
</div>


</div>


---


# Explore the Archive


<div style="
display:grid;
grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
gap:25px;
margin:35px 0;
">


<div style="
border:1px solid #ddd;
padding:25px;
border-radius:10px;
">


<h3>
🗺 Interactive Map
</h3>


<p>
Explore the geographical distribution of heritage sites documented through field research.
</p>


<a href="/fieldwork-map/">
Open Map →
</a>


</div>



<div style="
border:1px solid #ddd;
padding:25px;
border-radius:10px;
">


<h3>
📚 Research Framework
</h3>


<p>
Understand how these sites are analyzed through space, narrative, materiality, and participation.
</p>


<a href="/field-research/">
Explore Research →
</a>


</div>


</div>



---


# Research Framework


The archive is organized through interconnected research perspectives:


<div style="
display:grid;
grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
gap:20px;
">


<div>

<h3>
01. Spatial Scale
</h3>

<p>
How architecture and spatial organization influence emotional distance.
</p>

</div>



<div>

<h3>
02. Narrative Structure
</h3>

<p>
How exhibitions and storytelling guide historical interpretation.
</p>

</div>



<div>

<h3>
03. Material Proximity
</h3>

<p>
How objects, replicas, and conservation practices create connections with the past.
</p>

</div>



<div>

<h3>
04. Participatory Memory
</h3>

<p>
How communities and younger generations continue historical memory.
</p>

</div>


</div>



---


# Browse the Archive



<div class="fieldwork-filters">


<label for="fieldwork-category">
Category
</label>


<select id="fieldwork-category">

<option value="">
All categories
</option>


{% for category in site.data.fieldwork.categories %}

<option value="{{ category }}">
{{ category }}
</option>

{% endfor %}


</select>




<label for="fieldwork-period">
Period
</label>


<select id="fieldwork-period">


<option value="">
All periods
</option>


{% assign periods = site.data.fieldwork.sites | map: "period" | flatten | uniq | sort %}


{% for period in periods %}

<option value="{{ period }}">
{{ period }}
</option>


{% endfor %}


</select>





<label for="fieldwork-lens">
Research Lens
</label>


<select id="fieldwork-lens">


<option value="">
All lenses
</option>


{% for lens in site.data.fieldwork.research_lenses %}


<option value="{{ lens }}">
{{ lens }}
</option>


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


{% if item.location.city %}

<span>
{{ item.location.city }}
</span>

{% endif %}



{% if item.location.province %}

<span>
{{ item.location.province }}
</span>

{% endif %}


</div>



<h2>
{{ item.name_en }}
</h2>



<p class="fieldwork-card__zh">

{{ item.name_zh }}

</p>



<p class="fieldwork-card__category">

{{ item.category.primary }}

</p>



<div class="fieldwork-card__lenses">


{% for lens in item.research_lens %}


<span class="research-tag">

{{ lens }}

</span>


{% endfor %}


</div>



{% if item.field_research.years.size > 0 %}


<p class="fieldwork-card__visited">

Visited:
{{ item.field_research.years | join: ", " }}

</p>


{% endif %}



</article>


{% endfor %}



</div>





<script>


document.addEventListener("DOMContentLoaded", function () {


const category =
document.getElementById("fieldwork-category");


const period =
document.getElementById("fieldwork-period");


const lens =
document.getElementById("fieldwork-lens");


const cards =
Array.from(document.querySelectorAll(".fieldwork-card"));


const count =
document.getElementById("fieldwork-count");




function filterSites(){


let visible = 0;



cards.forEach(card => {


const okCategory =
!category.value ||
card.dataset.category === category.value;



const okPeriod =
!period.value ||
card.dataset.period.split("|").includes(period.value);



const okLens =
!lens.value ||
card.dataset.lenses.split("|").includes(lens.value);



const show =
okCategory &&
okPeriod &&
okLens;



card.hidden =
!show;



if(show){
visible++;
}


});



count.textContent =
`Showing ${visible} site${visible === 1 ? "" : "s"}`;


}



[category,period,lens]
.forEach(select =>
select.addEventListener(
"change",
filterSites
));


});


</script>
