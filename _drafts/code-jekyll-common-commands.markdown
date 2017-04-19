---
layout: post
title:  "Jekyl Love"
date:   2017-03-14 10:00:30 -0500
category: blog
tags: 
- Jekyll

image: ../assets/blog-jekyll-love/blank-800x500.jpg

---

I'm using Jekyl to run this site. For years I'd been dreaming of a light weight website engine that would allow me to edit posts via a text editor versus web based GUI. I'd considered switching over from Wordpress to a static HTML site. I really hate the experience of editing posts via Wordpress's back end user interface. For simple text and image based posts the Wordpress backend is bloated and I write my articles in a simple text editor anyways so copy everything over ends up a redundant task.  

Having used Jekyll for a little over a year, I have to say that I'm hooked. Creating new sites is a breeze and customizing them is as easy as if I was hand coding a blank HTML page. I'm not saying that opensource website platforms like Wordpress and Drupal are bad or anything. 

I'm having such a good time with Jekyll that I thought that I would share a page that really challenged the limits of my Jekyll powers. 

If you're new to Jekyll here is a great resource on getting up and running:

Otherwise you'll need to be somewhat familiar with Jekyll, and Liquid for the remainder of this post to make sense. 

![My project in a timeline](/assets/blog-jekyll-love/scottnihill-com-timeline.jpg){: .float-right}

The page in question is my [projects timeline page]({{ "/projects-timeline/" | prepend: site.baseurl | prepend: site.url }}) where I listed the projects I've been involved organized in a timeline. Each project is color coded based on the type of project; orange are physically demanding projects, blue are more cerbral tasks; green are personal projects. I though this would give me insight into my patterns of behavious. Also where applicable, each project links to the projects page or where people can find more information on it.

The idea was that I would be able to see in a snapshot how my time had been occupied over the years. Down the road I'd like to put in key milestones to further anchor my experiences.   

So here is how I created it... 

<div style="clear: right"></div>

### References
* [Markdown reference](https://en.support.wordpress.com/markdown-quick-reference/)

### The Table
For the overall layout I chose to use a table because there would always be 12 collumns, one for each month in the year, each of which would be of an equal width. The code looks like this...

{% raw %}
~~~~
{% assign months = "J,F,M,A,M,J,J,A,S,O,N,D" | split: "," %}
<table class="table table-striped">
    <tr>
    {% for month in months %}
        <th style="width: 8.33%">{{month}}</th>
    {% endfor %}
    </tr>
</table>	
~~~~
{% endraw %}

First I assign the months as a string split into an array with a comma. Then I looped through each item to create a new column or `<th></th>`. To make sure they remain at an equal width I set their width percentage to a 12th of 100% or 8.33%. The end result of the above code produces the following...

<div>
	{% assign months = "J,F,M,A,M,J,J,A,S,O,N,D" | split: "," %}
	<table class="table table-striped">
		<tr>
			{% for month in months %}
				<th style="width: 8.33%">{{month}}</th>
			{% endfor %}
		</tr>
	</table>
</div>
<br>

### Positioning projects in the timeline
The next step was positioning each project on a table row so that it lined up with its start and end. To begin with I'll stick to an example where a project started and ended int he same year.    

<div class="projects-schedule">
	{% assign months = "J,F,M,A,M,J,J,A,S,O,N,D" | split: "," %}

	{% assign startMonth = 1 | plus: 0 %}
	{% assign endMonth = 10 | plus: 0 %}
	{% assign numberCols = endMonth | minus: startMonth %}

	<table class="table table-striped">
		<tr>
			{% for month in months %}
				<th style="width: 8.33%">{{month}}</th>
			{% endfor %}
		</tr>
		<tr class="projects">
			{% if startMonth != 0 %}
				<td colspan="{{ startMonth }}"></td>
			{% endif %}
			<td colspan="{{numberCols}}" class="bootstrap">
				<a href="http://embreate.com/project/nba.html" target="_blank">
					<div style="background-image:url(/assets/projects/nba-play-zone.jpg);background-position: center center;" >
						<span>NBA Play Zone</span>
					</div>
				</a>
			</td>
		</tr>
	</table>
<div>






	












