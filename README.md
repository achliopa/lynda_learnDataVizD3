# Learning Data Visualization with D3.js
This is the repository for my course Learning Data Visualization with D3.js. The full course is available on [LinkedIn Learning](https://www.linkedin.com/learning/learning-data-visualization-with-d3-js?trk=insiders_6787408_learning) and [Lynda.com](https://www.lynda.com/D3-js-tutorials/Learning-Data-Visualization-D3-js/594451-2.html)

[![Learning Data Visualization with D3.js](https://media-exp2.licdn.com/media-proxy/ext?w=1200&h=675&f=n&hash=SHP3LPoguHYq2Me6Y6a1n%2B9ywxk%3D&ora=1%2CaFBCTXdkRmpGL2lvQUFBPQ%2CxAVta5g-0R6plxVUzgUv5K_PrkC9q0RIUJDPBy-kUiGu_9SfZX7tfcLeZLSiol4XeSgJlQA3ee2rRjTkFI69LcLmY4Yx3A)](https://www.linkedin.com/learning/learning-data-visualization-with-d3-js?trk=insiders_6787408_learning)

Creating data-driven visualizations and infographics that run on multiple devices responsively is a tough challenge. The D3.js library has revolutionized visualization by making it easier to parse your data and add meaningful interactivity. You can bring your data to life using D3, a bit of HTML, CSS, and JavaScript, and some SVG graphics. In this course, senior staff author Ray Villalobos explores how the D3 library works, and how you can use it to parse data from different sources and create interactive, visually exciting infographics and visualizations. He reviews the basics—controlling HTML with jQuery-esque selections and modifying attributes through CSS—before moving on to working with SVG graphics, a top choice for graphics in D3 visualizations. He also covers working with D3 methods like scaling, events, transitions, and animations, as well as how to work with data, including connecting to external data sources.

## Instructions
This repository has branches for each of the videos in the course. You can use the branch pop up menu in github to switch to a specific branch and take a look at the course at that stage. Or you can simply add `/tree/BRANCH_NAME` to the URL to go to the branch you want to peek at. 

## Branches
The branches are structured so that they correspond to the videos in the course. So, for example if I name a branch `02_03b` then that branch corresponds to the second chapter and the third video in that chapter. The extra letter at the end of the name corresponds to the state of the branch. A `b` means that this is how the code looks at the beginning of the video, an `e` means that is how the code looked at the end of the video.

You may find additional branches that correspond to other states, so for example, you may see a `t`, which means this is a target branch. A target branch is something I use during development or updates of a course and it's for a branch that I'm working towards. For the purposes of taking a course, you may ignore any additional branches. The `master` branch usually has the state of the project as I'm working through it and the final state of the code when I finish the course. 

## Installing
1. Make sure you have these installed
	- [node.js](http://nodejs.org/)
	- [git](http://git-scm.com/)
2. Clone this repository into your local machine using the terminal (mac) or Gitbash (PC) `> git clone CLONEURL`
3. CD to the folder `cd FOLDERNAME`
4. Run `> npm install` to install the project dependencies
5. Run `> grunt` to start live preview server

## More Stuff
Check out some of my other courses on [LinkedIn Learning](https://www.linkedin.com/learning/instructors/ray-villalobos?trk=insiders_6787408_learning) and [lynda.com](http://lynda.com/rayvillalobos). You can follow me on [LinkedIn](https://www.linkedin.com/in/planetoftheweb/), read [my blog](http://raybo.org), [follow me on twitter](http://twitter.com/planetoftheweb), or check out my [youtube channel](http://youtube.com/planetoftheweb).

# Lynda.com Learing Data Visualization with D3.js

## Introduction

* clone project from https://github.com/planetoftheweb/d3
* npm install dependencies (gulp packager)
* add to package.json

```
  "scripts": {
    "start": "gulp"
  },
```

## Section 1

### What is D3

* Data Driven Visualizations
* Open Web Standards
* CSS selectors
* Function Chaining
* Easy Parsing
* Data Binding
* Transition & Animations

### Using D3 Selections

* Selecting the DOM: DOM Access, select(STR), selectAll(STR)
* STR: CSS selectors
* like query queryAll in Vanila JS
* chain action methods

```
d3.select('.temp').text('hot');
```

* css pseucoclass nth-child is 1 based

### Controlling HTML within selections

* text() modify text
* html() modify html
* append() appends elements
* insert() inserts eleemnts
* remove() remove elements
* in insert after the element we can specify where to add it
* first we select and then we control

### Modifying Attributes through CSS

* style() CSS styles
* classed() toggle classes
* attr() any attribute
* propery() any property

```
.style('border-radius', '5px');
```

* add a checked checkbox in each table row start

```
d3.selectAll('tr')
	.insert('td', ':first-child')
	.append('input')
	.attr('type', 'checkbox')
	.property('checked', true)
```

### Binding Data to the DOM 

* data() passes data to the function chain. data are consumed with callbacks

```
d3.selectAll('.day-high .temp')
	.data([32,33,54,55,66])
	html(function(d,i) {
		if(i===0) {
			return '<strong class="text-muted" style="font-size: 2rem">'+d+'</strong>';
		}
	return '<strong>'+d+'</strong>';
	})
```

### Creating Subselections

* enter() when we use enter we no longer work on the current selection but we create a new subselection
* exit() if we want to exit subselection and return to the parent selection 
* in the follwoing example we add rows to an empty table. the selectAll looks ito the future as these rows are created with append in the subselection

```
d3.select('tbody')
	.selectAll('tr')
	.data(myData)
	.enter().append('tr')
	.html(function(d) {
		return '<th scope="row">'+d.date+
		'</th><td>'+ d.low+'</td><td>'+d.high+'</td>'
})
```

## Section 2 - Understanding SVG Graphics

### Drawing with SVG

* SVG Graphics: HTML shapes lacking, XML format, Style through CSS, easy to create with Draw Software (Inkscape), scriptable w/ javascript

### Understanding SVG Primitives

* git checkout 02_02b
* wrap in <svg> tag with width and height attributes
* use style attribute to shape the svg : e.g. rect, circle, line, text, polyline
* g attribute creates groups
* any svg element can have id to be referenced
* href creates an instance a copy of another element
* example:

```
<svg width="600" height="400" style="background: #93A1A1">
          <line x1="0" y1="200" x2="600" y2="200"
            style="stroke: #26BBD2; stroke-width: 40px;"
          />
          <rect 
            x="200" y="100"
            width="200" height="200"
            style="fill: #CB4B19;"
          />
          <circle 
            cx="300" cy="200" r="100"
            style="fill: #840043;"
          />
          <text
            x="10" y="390"
            font-family="sans-serif"
            font-size="25"
            fill="white"
          >
            Hello SVG
          </text>
          <g id="triangle">
            <polyline 
              points="10 35, 30 10, 50 35"
              style="fill: #F7B330"
            />
          </g>
          <use href="#triangle" x="30" y="0" />

        </svg>
```

### Drawing SVG graphics with D3

* git checkout 02_03b
* target the DOM
* use append() to add SVG eleemnts or insert() tp add items in the elelment
* use attr() , style() etc to add properties to the eleement
* we run our code to add SVGs with D3 entrirely in JS (script.js)

```
d3.select('#viz')
  .append('svg')
    .attr('width', 600)
    .attr('height',400)
    .style('background', '#93A1A1')
  .append('rect')
    .attr('x', 200)
    .attr('y',100)
    .attr('width', 200)
    .attr('height',200)
    .style('fill', '#CB4B19');

d3.select('#viz svg')
  .append('circle')
    .attr('cx',300)
    .attr('cy',200)
    .attr('r',50)
    .style('fill','#840043');
```

* note that append() goes in one level so if we want to insert multiple primiticves in the svg we need to repeat selection to avoid nesting in elements

### Creating a simble SVG bar chart

* the result code

```
var bardata = [20, 30, 45, 15];
var height = 400,
  width = 600,
  barWidth = 50,
  barOffset = 5;

d3.select('#viz')
  .append('svg')
    .attr('width', width)
    .attr('height', height)
    .style('background', '#C9D7D6')
.selectAll('rect').data(bardata)
  .enter().append('rect')
    .style('fill','#C61C6F')
    .attr('width', barWidth)
    .attr('height', function(d) {
      return d;
    })
    .attr('x', function(d, i) {
      return i* (barWidth + barOffset);
    })
    .attr('y', function(d) {
      return height - d;
    });

```

* we first set our variables and an array of numbers for the chart
* we target the container div, and we append an svg hich we style with d3
* we preselect the bars as rectangles and we bind the array to them with data(). we enter() the subelement of svg and we append the rects 
* we add the sttic attrtibutes and for the dataarray dependent we use the callback. namely the height the x and y positions
* note that canvas axis origin is top left so we need to reverse some numbers

## Section 3. Using D3 Methods

### Adding a linear scale

* transform our data to fit in a predefined scale
* scaleLinear() is a continuous scale it maps a continous input series of numbers to a continuous output
* domain() is an array of values we fit in our scale, the original values to be modified
* range() another set of values we feed in the linear scale, represents the values we want to scale our data to.
* we can use some statistical value sto the scale like min() or max()
* https://github.com/d3/d3-array/blob/master/README.md#statistics

```
var bardata = [20, 30, 45, 15];
var height = 400,
    width = 600,
    barWidth = 50,
    barOffset = 5;

var yScale = d3.scaleLinear()
  .domain([0, d3.max(bardata)])
  .range([0, height]);

d3.select('#viz').append('svg')
  .attr('width', width)
  .attr('height', height)
  .style('background', '#C9D7D6')
.selectAll('rect').data(bardata)
  .enter().append('rect')
    .style('fill', '#C61C6F')
    .attr('width', barWidth)
    .attr('height', function(d) {
      return yScale(d);
    })
    .attr('x', function(d, i) {
      return i*(barWidth + barOffset)
    })
    .attr('y', function(d) {
      return height - yScale(d);
    });
```

* in the above example we set the height of the barchart relative to the container height using a new yScale based on the d3 linearScale.
* domain sets the input and range the output of the scale

### Using ordinal scales

*