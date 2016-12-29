---
layout: post
title:  "Ecosystem: An Evolving Bug Simulation"
date:   2016-12-26 10:00:30 -0500
category: project
tags: 
- Processing
- Evolving

image: ../assets/ecosystem-v0-4-screen-capture-00.jpg
---

I've been interested in computer generated evolving natural systems for a long time and wanted to play around with some of the principles myself. 

I found a great tutorial titled <a target="_blank" href="http://natureofcode.com/book/introduction/">The Nature of Code</a> by Daniel Shiffman which does a great job of providing beginner or more advanced programmers a step by step guide by which code can be used to simulate phenomena in the natural world. 

### Objective
Going into the process my objective was to create a system that would evolve on it's own and could be affected in some way by user input. I started with a plant and bug motif using simplified geometric shapes to conotate both the plants and bugs physical form. 

### Design
<div class="row">
  	<div class="col-sm-4 col-xs-8 col-sm-offset-0 col-xs-offset-2">
  		<video width="100%" height="auto" autoplay loop>
		   	<source src="../assets/ecosystem-v0-4-video-capture-bug-life-cycle.mp4" type="video/mp4">
		</video> 
  	</div>
  	<div class="col-sm-8 col-xs-12">
		<span class="label label-success">Plants</span> are drawn as green circles that get larger over time and once they reach a size threshold reproduce if there is an available space next to them. <br><span class="label label-danger">Bugs</span> are also circles, but can be any color and have two lines protruding from their body to represent antenna's. The bugs can reproduce when they have eaten enough food (plants), as indicated by a white circle at the center of their body. The antennas have sensors at the end that light up when they come into contact with food or another bug. A bug's characteristics are all variable; body size, antena length & spread, color etc. And these unique qualities are passed down when they reproduce with a little bit of mutation applied to the result. I was curious whether or not the bugs would evolve to find the optimal physical characteristics for long term survival.   
	</div>
</div>

### Result
When the simulation first launches the bugs consume the plants, reproduce rapidly until there is not enough resources to sustain the colony, they die off, the plants grow again and the cycle repeats. 
<div class="row">
	<div class="col-sm-8 col-xs-8 col-sm-offset-2 col-xs-offset-0">
		<video width="100%" height="auto" autoplay loop>
		   	<source src="../assets/ecosystem-v0-4-video-capture-fast-forward.mp4" type="video/mp4">
		</video>  
	</div>
</div>
In the above video you can see the plants starting to take over and then a growing swarm of bugs decimate the vegetation, and repeats over and over again. Though, the bugs find a stable equilibrium eventually.

![Ecosystem v0.4 data chart showing stabilization](/assets/ecosystem-v0-4-data-quantity-plants-bugs-over-time-chart.jpg){: .img-responsive}

The chart above shows the number of bugs and plants over time, and you can see early on there are massive die offs that are preceded by spikes in the plant population. The bugs do not have the capacity to control their compulsion to eat and reproduce so an abundance of food can lead to a population explosion. Once all the food is gone, the bugs will either starve or fight one another for survival. This leads to a massive die off until the plants have enough space to grow. 

At this point I have not built-in any evolutionary capacity for plants, so it is up to the bugs to evolve to a state where their characteristics result in sustainable populations. So what are the attributes that lead to such a stable state? And is there one optimal set? Or a number of different variations that could lead to a balanced system?  

![Ecosystem v0.4 data chart showing stabilization](/assets/ecosystem-v0-4-data-max-speed-at-death-chart.jpg){: .img-responsive}

In scrubbing the data output I found that the max speed of the bugs levels off around the same time the bug and plant populations stabalize. This could mean that faster bugs are too good at mating and eating so leads to an imbalance. So possibly after a massive die off a successful trait was found and it stuck. I'd have to spend much more time analysing the data to come to any firm conclusions.

### The Data
If you'd like to play around with the simulation or the data to see what patterns of behaviour you can uncover, I've placed links to bother the source code and a sample data output below. 

<a style="width:250px; margin: 5px" class="btn btn-lg btn-success" target="_blank" href="https://github.com/scottnihill/ecosystem"><i class="fa fa-github fa-2x fa-pull-left" aria-hidden="true"></i>Github repository</a>
<a style="width:250px; margin: 5px" class="btn btn-lg btn-success" target="_blank" href="https://github.com/scottnihill/ecosystem/blob/master/data-exports/bugData_v0.2_2016-4-10.csv"><i class="fa fa-file-text-o fa-2x fa-pull-left" aria-hidden="true"></i> CSV data file</a>

See below a description of the data attributes that can be found in the CSV file.

### The Simulations

I've documented the built in behaviours and attributes of the simulations elements. 

#### Bugs
<table class="table table-striped">
  	<tr>
		<th>Property</th>
		<th>Value Type</th>
		<th>Value Range</th>
		<th style="width: 35%">Description</th>
	</tr>
	{% for attribute in site.data.ecosystem-attributes %}
	<tr>
		<td>{{ attribute.property }}</td>
		<td>{{ attribute.value-type }}</td>
		<td>{{ attribute.value-range }}</td>
		<td>{{ attribute.description }}</td>
	</tr>
	{% endfor %}
</table>

##### Behavior

There are two states to a bug -- eating and reproducing -- that dictates their behavior. 

A bug will prioritise <span class="label label-success">Eating</span> when they are 80% or less their maximum size. Their antennas will only respond to food sources and they will be unable to reproduce. 

Once they've eaten to 80% or more of their max size they will focus explusively on <span class="label label-warning">Reproducing</span>, their antenna will only respond to other bugs and they will feed only if they pass over a food source, though will not slow down over it. They can only reproduce with a bug who is in reproduction mode. Reproduction causes them to lose 50% of their weight. 

There is currently no limit to who a bug can or can't <span class="label label-warning">Breed</span> with. 
Bugs will <span class="label label-danger">Fight</span> if they make contact with another bug whose color is sufficiently different from its own. A bugs color is not tied to any of their attributes though it is passed down through reproduction, so can be used to label bugs of different lineages.

<span class="label label-danger">Canabilism</span> is currently not allowed, bugs can kill one another but they can't eat them. 

### Next Steps
#### Version 0.4
There are a few more minor aesthetic tweaks I'd like to make; 

* Bugs:
	* Make sure that if a bugs body is over food that it detects it and stops.
	* Reproductive circle more noticeable
	* The chance the bugs will kill similar bugs becomes variable through evolutation
	* Bugs can kill each other if they get hungry
	* Make sure size affect how much food is required
* Stats:
	* Active bug doesn't change if others die off
	* Simulation Lifetime in hours and minutes
	* Keep track of total plant and bug wipeouts
	* Follow active bug visualization

#### Version 0.5
With the basic actions of one species complete I'd like to work on taking the experience to the next level. 

* Make the installation motion responsive. For this I'll need to think about how a person can interact with it (i.e. their shadow causes plants to shrink in size)
* Plants can evolve. Having two entities that can adapt to an environment will make things more interesting. 







