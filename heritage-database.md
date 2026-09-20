---
title: "Heritage Database"
layout: single
permalink: /heritage-database/
toc: false
sidebar:
  nav: "fieldwork-categories"
---


<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css">

<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>


<p style="
font-size:1.5em;
font-style:italic;
color:#555;
">
75 Heritage Sites Across China
</p>



This archive documents my longitudinal fieldwork across historical sites, museums, memorial spaces, religious sites, architectural heritage, and cultural landscapes across China.


Rather than treating heritage sites as isolated destinations, this database examines how places construct historical memory through spatial organization, material experience, narrative interpretation, and public participation.



<br>


---


# Archive Overview



<div style="
display:flex;
gap:70px;
flex-wrap:wrap;
margin:40px 0;
">


<div>
<h1>75</h1>
<p>Documented Sites</p>
</div>


<div>
<h1>6</h1>
<p>Site Categories</p>
</div>


<div>
<h1>8</h1>
<p>Research Lenses</p>
</div>


</div>



---


# Interactive Map



Explore the geographical distribution of my fieldwork sites across China.



<div id="heritage-map"
style="
height:600px;
width:100%;
margin:40px 0;
border-top:1px solid #999;
border-bottom:1px solid #ddd;
">
</div>



<p style="
font-size:0.9em;
color:#777;
">
Map visualization based on documented heritage sites in the fieldwork archive.
</p>



---


# Browse Archive



<label>
Category
</label>

<br>


<select id="category-filter">


<option value="">
All Categories
</option>


{% for category in site.data.fieldwork.categories %}


<option value="{{ category }}">
{{ category }}
</option>


{% endfor %}


</select>



<br>
<br>



<label>
Research Lens
</label>

<br>


<select id="lens-filter">


<option value="">
All Research Lenses
</option>


{% for lens in site.data.fieldwork.research_lenses %}


<option value="{{ lens }}">
{{ lens }}
</option>


{% endfor %}


</select>



<br>
<br>


<p id="site-count">

Showing {{ site.data.fieldwork.sites.size }} sites

</p>



---


# Site Catalogue



<div id="site-list">


{% for item in site.data.fieldwork.sites %}



<div class="heritage-entry"

data-category="{{ item.category.primary | escape }}"

data-lens="{{ item.research_lens | join:'|' | escape }}"

style="
padding:45px 0;
border-top:1px solid #ddd;
">


<p style="
font-size:0.85em;
letter-spacing:2px;
color:#777;
">

SITE {{ forloop.index }}

</p>



<h2>
{{ item.name_en }}
</h2>



<p style="
font-size:1.15em;
">

{{ item.name_zh }}

</p>



<p>

{{ item.location.city }}, {{ item.location.province }}

</p>




<p>

<strong>
Category
</strong>

<br>

{{ item.category.primary }}

</p>




{% if item.period %}

<p>

<strong>
Historical Period
</strong>

<br>

{{ item.period | join:", " }}

</p>

{% endif %}





<p>

<strong>
Research Themes
</strong>

</p>



{% for lens in item.research_lens %}


<span style="
border:1px solid #999;
padding:5px 10px;
margin-right:6px;
font-size:0.85em;
display:inline-block;
">


{{ lens }}


</span>


{% endfor %}



</div>



{% endfor %}



</div>





<script>


// ==============================
// Leaflet Interactive Map
// ==============================


var map = L.map('heritage-map')
.setView(
[35.8617,104.1954],
4
);



L.tileLayer(
'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
{
attribution:
'&copy; OpenStreetMap contributors'
}

).addTo(map);





{% for item in site.data.fieldwork.sites %}



{% if item.location.latitude and item.location.longitude %}



L.marker([

{{ item.location.latitude }},

{{ item.location.longitude }}

])


.addTo(map)



.bindPopup(


"<div style='min-width:240px'>" +


"<h3>{{ item.name_en }}</h3>" +


"<p><strong>{{ item.name_zh }}</strong></p>" +


"<p>{{ item.location.city }}, {{ item.location.province }}</p>" +



"<hr>" +



"<p><strong>Category</strong><br>" +

"{{ item.category.primary }}</p>" +



"<p><strong>Research Themes</strong><br>" +



"{% for lens in item.research_lens %}"

+
"{{ lens }}<br>"

+
"{% endfor %}"



+
"</p>" +


"</div>"


);



{% endif %}



{% endfor %}






// ==============================
// Database Filter
// ==============================



const category =
document.getElementById(
"category-filter"
);



const lens =
document.getElementById(
"lens-filter"
);



const entries =
document.querySelectorAll(
".heritage-entry"
);



const count =
document.getElementById(
"site-count"
);





function filterSites(){



let visible = 0;



entries.forEach(

function(entry){



let categoryMatch =

!category.value ||

entry.dataset.category === category.value;



let lensMatch =

!lens.value ||

entry.dataset.lens.includes(lens.value);





if(categoryMatch && lensMatch){


entry.style.display="block";

visible++;


}

else{


entry.style.display="none";


}


}

);



count.innerHTML =
"Showing "
+
visible
+
" sites";



}




category.addEventListener(
"change",
filterSites
);



lens.addEventListener(
"change",
filterSites
);



</script>
