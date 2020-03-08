---
layout: default
title: How to build a tooltip bar chart with d3?
description: This is a step-by-step instruction to build a tooltip bar chart with d3.
---

## Step 1: Start with an empty HTML file
```html
<!DOCTYPE html>
<meta charset="utf-8">
<head></head>
<body></body>
```
Add the following style sheet before the HTML body section to adjust the CSS style for the body to make sure the body section will be visible.
```javascript
<!DOCTYPE html>
<meta charset="utf-8">
<style>
  body {
        font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
        width: 960px;
        height: 500px;
        position: relative;
    }
</styel>
<head></head>
<body></body>
```

## Step2: Set up D3
By including D3 library in the head, we will be able to use the components from D3 library.

```javascript
<head>
<script src="https://d3js.org/d3.v3.min.js"></script>
</head>
```

## Step 3: Prepare the data set
Here we are using the dataset from Singapore 2019 GES, the faculty emplotment rate. We will add the sample data into the body script section.

```javascript
<body>
  <script>
    data = [
      {
        faculty: 'Faculty of Engineering',
        value: 89.6
      },
      {
        faculty: 'NUS Business School',
        value: 96.35
      },
      {
        faculty: 'School of Design & Environment',
        value: 91.8
      },
      {
        faculty: 'Yong Lon Lin School (Medicine)',
        value: 98.8
      },
      {
        faculty: 'School of Computing',
        value: 95.9
      },
      {
        faculty: 'Faculty of Science',
        value: 88.5
      },
      {
        faculty: 'Faculty of Arts & Social Sciences',
        value: 88
      },
      {
        faculty: 'Yale-NUS College',
        value: 95.35
      },
      {
        faculty: 'Multi-Disciplinary Programmes',
        value: 90.65
      },
      {
        faculty: 'Faculty of Dentistry',
        value: 100
      },
      {
        faculty: 'Faculty of Law',
        value: 95.7
      },
      {
        faculty: 'YST Conservatory of Music',
        value: 82.6
      }
    ];
  </script>
</body>
```

## Step 4: Set up the view port
Add the following code into your body _script_ following the dataset. This will help to adjust the chart svg postion and we are building a new svg here.

```javascript
  var axisMargin = 20,
            margin = 40,
            valueMargin = 4,
            width = parseInt(d3.select('body').style('width'), 10),
            height = parseInt(d3.select('body').style('height'), 10),
            barHeight = (height-axisMargin-margin*2)* 0.4/data.length,
            barPadding = (height-axisMargin-margin*2)*0.6/data.length,
            data, bar, svg, scale, xAxis, facultyWidth = 0;
            
  max = d3.max(data, function(d) { return d.value; });

  svg = d3.select('body')
            .append("svg")
            .attr("width", width)
            .attr("height", height);
```

Add the following codes into the _style sheet_ for svg
```javascript
    svg {
        width: 100%;
        height: 100%;
        position: center;
    } 
```


## Step 5: Load data into svg chart
Add the following codes below the svg in the _script_
```javascript
 bar = svg.selectAll("g")
            .data(data)
            .enter()
            .append("g");
```

## Step 6: Define the axis scale and display the axis domain
Add the following codes in the _script_
```javascript
  bar.append("text")
            .attr("class", "label")
            .attr("y", barHeight / 2)
            .attr("dy", ".35em") //vertical align middle
            .text(function(d){
                return d.label;
            }).each(function() {
        labelWidth = Math.ceil(Math.max(labelWidth, this.getBBox().width));
    });
    
  scale = d3.scale.linear()
            .domain([0, max])
            .range([0, width - margin*2 - labelWidth]);
    
  xAxis = d3.svg.axis()
            .scale(scale)
            .tickSize(-height + 2*margin + axisMargin)
            .orient("bottom"); 
```

## Step 7: Display the bar chart
Add the following codes in the _script_ to show the bars
```javascript
  bar.append("rect")
            .attr("transform", "translate("+labelWidth+", 0)")
            .attr("height", barHeight)
            .attr("width", function(d){
                return scale(d.value);
            });
            
   bar.attr("class", "bar")
            .attr("cx",0)
            .attr("transform", function(d, i) {
                return "translate(" + margin + "," + (i * (barHeight + barPadding) + barPadding) + ")";
                         });
```

Continue adding the following codes to display the percentage for each bars
```javascript
  bar.append("text")
            .attr("class", "value")
            .attr("y", barHeight / 2)
            .attr("dx", -valueMargin + labelWidth) //margin right
            .attr("dy", ".35em") //vertical align middle
            .attr("text-anchor", "end")
            .text(function(d){
                return (d.value+"%");
            })
            .attr("x", function(d){
                var width = this.getBBox().width;
                return Math.max(width + valueMargin, scale(d.value));
            }); 
```

Besides, add the following codes into the _style sheet_ to make text visible and change the bar color
```javascript
    text {
        font: 10px sans-serif;
        color: white;
    }
    
    text.value {
        font-size: 120%;
        fill: white;
    }
    
    .bar {
        fill: steelblue;
        fill-opacity: .9;
    } 
```

## Step 8: Display chart background grid line
Add the following codes into the _script_
```javascript
  svg.insert("g",":first-child")
            .attr("class", "axisHorizontal")
            .attr("transform", "translate(" + (margin + labelWidth) + ","+ (height - axisMargin - margin)+")")
            .call(xAxis);
```

Besides, add the following codes into the _style sheet_ 
```javascript
    .axisHorizontal path{
        fill: none;
    }
    
    .axisHorizontal .tick line {
        stroke-width: 1;
        stroke: rgba(0, 0, 0, 0.2);
    }
```

## Step 9: Add on tooltip for the bar chart
Add the following codes into the _script_
```javascript
  var div = d3.select("body").append("div").attr("class", "toolTip");
   
   bar.on("mousemove", function(d){
                div.style("left", d3.event.pageX+10+"px");
                div.style("top", d3.event.pageY-25+"px");
                div.style("display", "inline-block");
                div.html((d.label)+"<br>"+(d.value)+"%");
            });
            
    bar.on("mouseout", function(d){
                div.style("display", "none");
            }); 
```

Besides, add the following codes into the _style sheet_ 
```javascript
  .toolTip {
        font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
        position: absolute;
        display: none;
        width: auto;
        height: auto;
        background: none repeat scroll 0 0 white;
        border: 0 none;
        border-radius: 8px 8px 8px 8px;
        box-shadow: -3px 3px 15px #888888;
        color: black;
        font: 12px sans-serif;
        padding: 5px;
        text-align: center;
    }
   
```

We are DONE!

You can visit her for the [DEMO](./viz.html). 
Here is the [source code](https://github.com/Livian1107/CS5346/blob/master/viz.html).

Thank you!


_March 8, 2020_

[back](./)
