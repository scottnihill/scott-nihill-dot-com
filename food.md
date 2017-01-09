---
layout: page
title: Weekly Meals
permalink: /weekly-meals/
---

I've gotten into the habit of cooking meals for the entire week. I decided that I would keep track of my meal plans and the recipes that inspired them so I don't lose track of my favorites. 

<div>
	{% assign weekData = site.data.weekly-meals | group_by: 'week-number' %}
	{% for week in weekData %}
		<div class="row">
		{% for meal in week.items %}
			{% if meal.recipe1 != null %}
			<a href="{{ meal.recipe1 }}" target="_blank">
			{% endif %}
				<div class="col-sm-4" style="{% if meal.image != null %}background-image: url(/assets/recipes/{{meal.image}});{% endif %} background-position: center center; background-size: cover;height: 150px">
					<!--{{ meal.title }}-->
				</div>
			{% if meal.recipe1 != null %}
			</a>
			{% endif %}
		{% endfor %}
		</div>
	{% endfor %}
</div>

