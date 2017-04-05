---
layout: page
title: Projects
permalink: /projects-list/
navigationActive: false

---

{% comment %} 
	Data found in 'Google Drive / Vital scottnihill.com / SN scottnihill.com - projects'  
	Data src: https://docs.google.com/spreadsheets/d/1hXXyJMGAxXfqY6p4ZoHZ5Cdhlite_lKjJAalYAySO0c/edit#gid=670251319
{% endcomment %}

<div>
	<div>
		<a class="btn btn-default" href="{{ post.url | prepend: site.baseurl }}/projects-grid"><i class="fa fa-th" aria-hidden="true"></i> Grid</a>
		<a class="btn btn-default active" href="{{ post.url | prepend: site.baseurl }}/projects-list"><i class="fa fa-list" aria-hidden="true"></i> List</a>
		<a class="btn btn-default" href="{{ post.url | prepend: site.baseurl }}/projects-timeline"><i class="fa fa-calendar" aria-hidden="true"></i> Timeline</a>
	</div>
	<br>

	{% assign projects = site.data.projects | sort:"date-end" | reverse %}
	{% assign colNumber = 1 | plus: 0 %}
	{% for project in projects %}
		{% if project.status == "1 hold" %}
		{% elsif project.status == "0 closed" %}
		{% else %}
			
			<div class="row">
				<div class="col-xs-2">
					{% if project.image != null %}
					<img class="img-responsive" src="/assets/projects/{{project.image}}-800x500.jpg">
					{% else %}
					<img class="img-responsive" src="/assets/projects/blank-800x500.jpg">
					{% endif %}
				</div>
				<div class="col-xs-10">
					<h4>{{project.title}}</h4>
					{% if project.portfolio != null %}
					<a href="{{project.portfolio}}">
						MORE &nbsp;<i class="fa fa-external-link" aria-hidden="true"></i>
					</a>
					{% endif %}

				</div>
			</div>
			<br>
			
		{% endif %}
	{% endfor %}
</div>






