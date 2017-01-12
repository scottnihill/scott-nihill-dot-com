---
layout: page
title: Projects
permalink: /projects/
---

I'm going through the process of archiving the projects that I've been involved in over the years and thought that I'd summarize everything into a timeline / gantt chart. Each project reference will link to a page with more information where applicable. To begin with the chart will be static but soon I'll tie it into the Google Sheet where the information is kept. 

{% assign currentYear = 2017 %}
{% assign months = "1,2,3,4,5,6,7,8,9,10,11,12" | split: "," %}
<table class="table table-striped">
  	<tr>
		{% for month in months %}
			<th style="width: 8.33%">{{month}}</th>
		{% endfor %}
	</tr>
	<!-- 2016 -->
	<tr>
		<td class="bg-grey" colspan="12">2016</td>
	</tr>
	<tr>
		<td colspan="10"></td>
		<td class="personal" colspan="2">
			<a href="http://scottnihill.com/project/penis-pinecone-block-print-xmas-paper.html">
				Xmas Paper
			</a>
		</td>
	</tr>
	<tr>
		<td colspan="8"></td>
		<td class="embreate" colspan="4">Lee Memorial</td>
	</tr>
	<tr>
		<td colspan="6"></td>
		<td class="embreate" colspan="2">Jelly Belly</td>
	</tr>
	<tr>
		<td colspan="2"></td>
		<td class="embreate" colspan="2">Mediummune</td>
	</tr>
	<tr>
		<td class="embreate" colspan="6">NBA</td>
	</tr>
	<tr>
		<td class="personal" colspan="3">Side Tables</td>
	</tr>
	<!-- 2015 -->
	<tr>
		<td class="bg-grey" colspan="12">2015</td>
	</tr>
	<tr>
		<td colspan="11"></td>
		<td class="embreate" colspan="1">NBA</td>
	</tr>
	<tr>
		<td class="embreate" colspan="12">Hellions</td>
	</tr>
	<tr>
		<td colspan="9"></td>
		<td class="bootstrap" colspan="3">Kensington</td>
	</tr>
	<tr>
		<td colspan="6"></td>
		<td class="bootstrap" colspan="5">Campari</td>
	</tr>
	<tr>
		<td colspan="6"></td>
		<td class="embreate" colspan="2">Bravetail</td>
	</tr>
	<tr>
		<td colspan="1"></td>
		<td class="personal" colspan="2">Filey & Walkr</td>
	</tr>
</table>

<!--
	{% assign yearData = site.data.projects-schedule | group_by: 'year' %}
	{% for year in yearData %}
		{% for project in year.items %}
			{{ project.title }}
		{% endfor %}
	{% endfor %}
-->



