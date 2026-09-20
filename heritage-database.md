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
font-size:1.4em;
font-style:italic;
color:#555;
line-height:1.8;
">
75 Heritage Sites Across China
</p>



This database documents my longitudinal fieldwork across historical sites, museums, memorial spaces, religious sites, architectural heritage, and cultural landscapes in China.


Rather than presenting heritage sites as isolated destinations, this archive explores how different environments shape historical understanding, emotional experience, and public engagement.



<br>
<br>



---


# Database Overview


<div style="
display:flex;
gap:60px;
margin:40px 0;
flex-wrap:wrap;
">


<div>

<h2>
75
</h2>

<p>
Heritage Sites
</p>

</div>


<div>

<h2>
6
</h2>

<p>
Categories
</p>

</div>


<div>

<h2>
8
</h2>

<p>
Research Lenses
</p>

</div>


</div>



<br>



---


# Browse Database



<label>
Category
</label>


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



&nbsp;&nbsp;



<label>
Research Lens
</label>


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


<div id="site-count">

Showing {{ site.data.fieldwork.sites.size }} sites

</div>



<br>


---


# Site Catalogue



<div id="site-list">



{% for item in site.data.fieldwork.sites %}



<div class="heritage-entry"
style="
border-top:1px solid #ddd;
padding:30px 0;
"
data-category="{{ item.category.primary }}"
data-lens="{{ item.research_lens | join:'|' }}"
>



<h2>
{{ item.name_en }}
</h2>


<p style="font-size:1.1em;">
{{ item.name_zh }}
</p>



<p>

{% if item.location.city %}

{{ item.location.city }}

{% endif %}


{% if item.location.province %}

· {{ item.location.province }}

{% endif %}

</p>



<p>
<strong>Category:</strong>

{{ item.category.primary }}

</p>



{% if item.period %}

<p>

<strong>Period:</strong>

{{ item.period | join:", " }}

</p>

{% endif %}



<br>


<p>
<strong>Research Lens:</strong>
</p>



{% for lens in item.research_lens %}

<span style="
border:1px solid #aaa;
padding:4px 10px;
margin-right:8px;
font-size:0.85em;
">

{{ lens }}

</span>


{% endfor %}



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



function filter(){


let visible = 0;



entries.forEach(
entry => {


let categoryOK =
!category.value ||
entry.dataset.category === category.value;



let lensOK =
!lens.value ||
entry.dataset.lens.includes(lens.value);



if(categoryOK && lensOK){

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
filter
);


lens.addEventListener(
"change",
filter
);



}

);

</script>
