---
layout: page
title: Projects
permalink: /projects-grid/
navigationActive: true

---

{% comment %} 
	Data found in 'Google Drive / Vital scottnihill.com / SN scottnihill.com - projects'  
	Data src: https://docs.google.com/spreadsheets/d/1hXXyJMGAxXfqY6p4ZoHZ5Cdhlite_lKjJAalYAySO0c/edit#gid=670251319
{% endcomment %}

<div>

	<div>
		<a class="btn btn-default active" href="{{ post.url | prepend: site.baseurl }}/projects-grid"><i class="fa fa-th" aria-hidden="true"></i> Grid</a>
		<a class="btn btn-default" href="{{ post.url | prepend: site.baseurl }}/projects-list"><i class="fa fa-list" aria-hidden="true"></i> List</a>
		<a class="btn btn-default" href="{{ post.url | prepend: site.baseurl }}/projects-timeline"><i class="fa fa-calendar" aria-hidden="true"></i> Timeline</a>
	</div>
	<br>

	{% assign projects = site.data.projects | sort:"date-end" | reverse %}
	{% assign colNumber = 1 | plus: 0 %}
	{% for project in projects %}
		{% if project.status == "1 hold" %}
		{% elsif project.status == "0 closed" %}
		{% else %}
			{% if colNumber == 1 %}
				<div class="row">
				{% endif %}
					<div class="col-sm-3">
						{% if project.portfolio != null %}
						<a href="{{project.portfolio}}">
						{% endif %}
							{% if project.image != null %}
							<img class="img-responsive" src="/assets/projects/{{project.image}}-800x500.jpg">
							{% else %}
							<img class="img-responsive" src="/assets/projects/blank-800x500.jpg">
							{% endif %}
							<h4>{{project.title}}
								{% if project.portfolio != null %}
								&nbsp;&nbsp;<i class="fa fa-external-link" aria-hidden="true"></i>
								{% endif %}
							</h4>
						{% if project.portfolio != null %}
						</a>
						{% endif %}
					</div>
				{% if colNumber == 4 %}
				</div>
				{% endif %}
				{% assign colNumber = colNumber | plus: 1 %}
				
				{% if colNumber == 5 %}
				{% assign colNumber = 1 | plus: 0 %}
			{% endif %}
		{% endif %}
	{% endfor %}
</div>






