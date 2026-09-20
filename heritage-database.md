---
title: "Heritage Database"
layout: single
permalink: /heritage-database/
toc: false
sidebar:
  nav: "fieldwork-categories"
---


<div id="top"></div>


# Heritage Database


<p style="
font-size:1.5em;
font-style:italic;
color:#555;
line-height:1.8;
margin-top:20px;
">
75 Heritage Sites Across China
</p>


This archive presents a longitudinal fieldwork database documenting historical sites, museums, memorial spaces, religious landscapes, and cultural heritage environments across China.


Through systematic observation and documentation, the database explores how heritage spaces construct historical memory through architecture, objects, narratives, and public engagement.



<br>
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

<h1>
75
</h1>

<p>
Documented Sites
</p>

</div>



<div>

<h1>
6
</h1>

<p>
Site Categories
</p>

</div>



<div>

<h1>
8
</h1>

<p>
Research Lenses
</p>

</div>



</div>



<br>


---


# Browse Archive



<div style="
margin:30px 0;
padding:25px 0;
border-top:1px solid #999;
border-bottom:1px solid #ddd;
">


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



</div>




<p id="site-count">

Showing {{ site.data.fieldwork.sites.size }} sites

</p>




<br>



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
color:#777;
letter-spacing:2px;
">

SITE {{ forloop.index | prepend: "00" | slice: -2, 2 }}

</p>




<h2>
{{ item.name_en }}
</h2>



<p style="
font-size:1.15em;
margin-top:-10px;
">

{{ item.name_zh }}

</p>



<br>



<p>

{% if item.location.city %}

{{ item.location.city }}

{% endif %}



{% if item.location.province %}

, {{ item.location.province }}

{% endif %}


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



<div>


{% for lens in item.research_lens %}



<span style="
display:inline-block;
border:1px solid #aaa;
padding:5px 12px;
margin:5px 5px 5px 0;
font-size:0.85em;
">


{{ lens }}


</span>



{% endfor %}


</div>




<br>



<a href="#">

View Research Entry →

</a>




</div>



{% endfor %}



</div>





<script>


document.addEventListener(
"DOMContentLoaded",
function(){


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



entries.forEach(function(entry){



const categoryMatch =
!category.value ||
entry.dataset.category === category.value;



const lensMatch =
!lens.value ||
entry.dataset.lens.includes(lens.value);



if(categoryMatch && lensMatch){


entry.style.display="block";

visible++;


}

else{


entry.style.display="none";


}



});



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



});


</script>
