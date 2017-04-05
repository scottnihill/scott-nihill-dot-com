---
layout: page
title: Blog
permalink: /blog/
navigationActive: true

---

<div class="m-b-l">
	{% assign colNum = 1 %}
	{% for post in site.posts %}
		{% if post.category != "blog" %} 
	  {% else %}
		  
		  {% if colNum == 1 %}
		  <div class="row">
		  {% endif %}
		    
	      <div class="col-md-4">
	        <a href="{{ post.url | prepend: site.baseurl }}">
	          <img class="img-responsive" src="{{ post.image }}">
	        </a>
	        <h4>
	          <a href="{{ post.url | prepend: site.baseurl }}">
	            {{ post.title }}
	          </a>
	        </h4>
	      </div>
	      
	    {% assign colNumber = colNum | plus: 1 %}
		  
		  {% if colNumber == 4 %}
		  	</div>
				{% assign colNumber = 1 | plus: 0 %}
			{% endif %}

		{% endif %}
	{% endfor %}
</div>


