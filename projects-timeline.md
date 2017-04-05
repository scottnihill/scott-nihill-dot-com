---
layout: page
title: Projects
permalink: /projects-timeline/
navigationActive: false

---

{% comment %} 
	Data found in 'Google Drive / Vital scottnihill.com / SN scottnihill.com - projects'  
	Data src: https://docs.google.com/spreadsheets/d/1hXXyJMGAxXfqY6p4ZoHZ5Cdhlite_lKjJAalYAySO0c/edit#gid=670251319
{% endcomment %}


<div>
	<a class="btn btn-default" href="{{ post.url | prepend: site.baseurl }}/projects-grid"><i class="fa fa-th" aria-hidden="true"></i> Grid</a>
	<a class="btn btn-default" href="{{ post.url | prepend: site.baseurl }}/projects-list"><i class="fa fa-list" aria-hidden="true"></i> List</a>
	<a class="btn btn-default active" href="{{ post.url | prepend: site.baseurl }}/projects-timeline"><i class="fa fa-calendar" aria-hidden="true"></i> Timeline</a>
</div>
<br>



<div class="projects-schedule">

	{% assign currentYear = 2019 %}
	{% assign months = "J,F,M,A,M,J,J,A,S,O,N,D" | split: "," %}
	{% assign projects = site.data.projects-schedule %}

	<table class="table table-striped">
	  	<!-- List Months -->
	  	<tr>
			{% for month in months %}
				<th style="width: 8.33%">{{month}}</th>
			{% endfor %}
		</tr>
		{% for counter in (0..50) %}
			{% assign yearHeaderCreated = false %}
			{% assign currentYear = currentYear | minus: 1 %}
			{% for project in projects %}

				<!-- Setup Variables -->
				{% assign projectStartYear = project.date-start | date: '%Y' %}
				{% assign projectStartYear = projectStartYear | minus: 0 %}
				{% assign projectEndYear = project.date-end | date: '%Y' %}
				{% assign projectEndYear = projectEndYear | minus: 0 %}

				{% assign startMonth = project.date-start | date: '%m' %}
				{% assign startMonth = startMonth | minus: 1 %}
				{% assign endMonth = project.date-end | date: '%m' %}
				{% assign endMonth = endMonth | minus: 1 %}
				{% assign active = false %}

				<!-- Check if project is within range -->
				{% if projectEndYear == currentYear %}
					<!-- does the project start and end on the same year-->
					{% assign active = true %}
					{% if projectStartYear != currentYear %}
						{% assign startMonth = 0 %}
					{% endif %}
					
				{% elsif projectStartYear == currentYear %}
					<!-- does the project start and end on the same year-->
					{% assign active = true %}
					{% if projectEndYear != currentYear %}
						{% assign endMonth = 12 %}
					{% endif %}

				{% elsif projectStartYear <= currentYear %}
					{% if projectEndYear >= currentYear %}
						{% assign active = true %}
						{% assign startMonth = 0 %}
						{% assign endMonth = 12 %}
					{% endif %}
				
				{% endif %}

				{% if active == true %}
					{% if yearHeaderCreated == false %}
						{% assign yearHeaderCreated = true %}
						<tr>
							<td class="bg-grey" colspan="12">{{currentYear}}</td>
						</tr>
					{% endif %}

					{% assign numberCols = endMonth | minus: startMonth %}

					<tr class="projects">
						{% if startMonth != 0 %}
							<td colspan="{{ startMonth }}"></td>
						{% endif %}
						<td colspan="{{numberCols}}" class="{{project.my-client | downcase}}">
							{% if project.portfolio != null %}<a href="http://scottnihill.com/project/penis-pinecone-block-print-xmas-paper.html" target="_blank">{% endif %}
								<div style="background-image:url(/assets/projects/{{project.image}});background-position: center center;" >
									<span>{{project.title}}</span>
								</div>
							{% if project.portfolio != null %}</a>{% endif %}
						</td>
					</tr>

				{% endif %}
			{% endfor %}
		{% endfor %}
	</table>
</div>






