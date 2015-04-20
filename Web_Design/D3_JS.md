### Basic D3 Methods

`selection.select(name)`, select first matched object.
`d3.selectAll(name)`, select all elements.

`selection.selectAll(name)`, select all matched object(s).

`selection.append(name)`, append a new element.

`selection.insert(name[, before])`, insert element with name before the matching element.

`selection.attr(name[, value])`, passing an object for value can set multiple attributes. If value is not specified, returns the value of the specified attribute.

`selection.style(name[, value[, priority]])`, set the CSS properties.

`selection.classed(name[, value])`, convenience routine for setting the "class" attribute. Passing object to set multiple `class` at a time. `{'foo': true, 'bar': false}` or `{'foo bar', true}`.

`selection.html([value])`, set innerHTML content and replace existing ones.

`selection.txt([value])`, setting the text content.

`selection.remove()`, remove element from document and return the removed element.

### SVG Basics

**MDN** SVG In HTML Introduction is [here](https://developer.mozilla.org/en/docs/SVG_In_HTML_Introduction).

SVG element reference is [here](https://developer.mozilla.org/en-US/docs/Web/SVG/Element).

SVG attribute reference is [here](https://developer.mozilla.org/en-US/docs/Web/SVG/Element).

```
<!-- CSS can be used to style SVG -->
<!-- The order goes from BACK to FRONT -->
<svg width='300' height='300' style="border: 1px solid black;">
  <!-- Draw rectangle -->
  <rect x="10" y="10" width="50" height="50" fill="blue"></rect>
  <rect x="0" y="0" width="1" height="1" fill="black"></rect>
  <!-- Draw circle -->
  <circle r="50" cx="100" cy="100" fill="ORANGE" stroke="RED" stroke-width="5"/>
  <!-- Draw ellipse -->
  <ellipse rx="150" ry="20" cx="150" cy="150" fill="WHITE" stroke="BLACK" stroke-width="5"/>
  <!-- Draw Text -->
  <text x="150" y="150" fill="BLACK" style="text-anchor: middle">D3 Is Cool!</text>
  <!-- Draw line -->
  <line x1="0" y1="150" x2="300" y2="150" stroke="BLUE" stroke-width="5"/>
  <!-- Draw polygon -->
  <polygon points="150,150 0,300 300,300" fill="BLACK" stroke="RED" stroke-width="5"/>
  <!-- Draw polyline: Does NOT Connect Begin and End Point -->
  <polyline points="75,200 150,150 225,200" fill="Olive" stroke="Purple" stroke-width="5"/>
  <!-- Path -->
  <!-- z for close the shape -->
  <path d="M 100 100 L 100 200 L 200 100 z" stroke-width="5" stroke="RGBA(4, 32, 41, 1)" fill="none"/>
</svg>
```

### Using Data

```
var dataset = [8, 48, 14, 31, 23, 13, 42, 63, 51, 80, 10, 23];

var svgWidth = 300, svgHeight = 200;
var numOfDataEntry = dataset.length;

svg = d3.select('body')
    .append('svg')
    .attr({
      width: svgWidth,
      height: svgHeight
    })
    .style({
      border: '1px solid black',
    });

svg.selectAll('rect')
   .data(dataset)
   .enter()
   .append('rect')
   .attr({
     x: function(d, i){
      return i * svgWidth/numOfDataEntry;
     },
     y: function(d, i){
      // turn chart into right position
      return (200 - svgHeight * (d / 100));
     },
     width: svgWidth/numOfDataEntry,
     height: function(d){
      return svgHeight * (d / 100);
     },
     fill: 'orange',
     stroke: 'black'
   });
```

### Updating Pattern

```
var svg = d3.select('body')
    .append('svg')
    .attr({
        width: 600,
        height: 200
    });

svg.selectAll('rect')
    .data(d3.range(5))
    .enter()
    .append('rect')
    .attr({
        width: 50,
        height: 100,
        y: 100,
        x: function(d, i) {
            return i * 51;
        },
        fill: 'black'
    });

var moreData = d3.range(10);
var rects = svg.selectAll('rect')
    .data(moreData);

rects.attr('fill', 'lightblue');

rects.data(moreData)
    .enter()
    .append('rect')
    .attr({
        width: 50,
        height: 100,
        y: 100,
        x: function(d, i) {
            return i * 51;
        },
        fill: 'black'
    });
    // attr ONLY apply to the newly created obj

rects.exit()
    .remove();
```

### Scales

**Part 01**

```
var svg = d3.select('body').append('svg').attr({
    width: window.innerWidth - 10,
    height: window.innerHeight - 100
});

var data = d3.range(100);

var heightScale = d3.scale.linear() // y = mx + b
    .domain([0, d3.max(data)])
    .range([0, window.innerHeight - 40]);

    var color = d3.scale.linear()
    .domain([0, d3.max(data)])
    .range(['yellow', 'red']);

svg.selectAll('rect').data(data).enter().append('rect').attr({
    width: 10,
    height: heightScale,
    x: function(d, i) {
        return i * 11;
    },
    y: 20,
    fill: color
});
```

**Part 02**

```
```