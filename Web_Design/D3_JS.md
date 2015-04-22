# Introduction

Data visualization is the fastest way to communicate with others.
The loop of write/render/evaluate is critical to the iterative process of refining a data visualization design.

# Introducing D3

[**D3**](http://d3js.org) (Data-Driven Documents), a JavaScript library for creating data visualization, is created by *Mike Bostock* and released under *BSD License*

**D3** does not generate predefined visualization (D3's *layouts* is a exception, it help to achieve common visualization forms quickly). It does not support older browsers , bit map tiles, hide original data.

## D3 Time-line

2005 - **perfuse**, a data visualization toolkit created by *Jeffrey Heer*, *Stuart Card*, and *James Landay* in Java running in browsers via Java plug-in.

2007 - **Flare** was introduced by *Jeffrey Heer*, written in ActuonScript view on web through Adobe Flash Player.

2009 - **Protovis** was introduced by *Jeffrey Heer* and *Michael Bostock*, written in JavaScript and expanded on **perfuse** and **Flare**.

2011 - **D3** was officially announced by *Jeffrey Heer*, *Michael Bostock* and *Vadim Ogievetsky*. It operates on the web document and provide easy debugging and experimentation, but with steeper leraning curve.

NOTE:  *Jeffrey Heer*, *Michael Bostock* and *Vadim Ogievetsky*'s **InfoVis** paper can be found [here](http://vis.stanford.edu/files/2011-D3-InfoVis.pdf).

## Alternatives

There are many alternatives you can find online. There is no best solution out there, but you can always find the most suitbale one.

# Technology Fundamentals

**Web Server**, Internet-connected computer running server software.
**Web Client** are Web browsers. **Web Page** can be identified by its **URL** (Uniform Resource Locator) or **URI** (Uniform Resource Identifier).

Complete URLs consiste of three(3) parts:
1. Communication protocol indicator, `HTTP` or `HTTPS`
1. Domain name
1. Additional locating information

## Required Knowledge Before Using D3

### HTML

***HTML*** is a tool for specifing semantic strcture, or attaching hierarchy, relationships, and meaning to content.

*Nested tags* introduinces hierarchy to the document. property/value pairs attributes can be included in all **HTML** opening tag. Different tags have different attributes, but some attributes can be assigned to any type `class` (Allow multiple) and `id` (Only allow one), use `id` if there will be only one such element. Self-closing tag is optional in **HTML5**.

NOTE: `id` and `class` name **MUST** begin with alphabetic character.
NOTE: Commenting is an easy way to reach out and providing guidance to your future self.

**DOM** refers to the hierarchical structure of **HTML**, and each bracket tag is an element.

INFO: **Chrome** and **Safari** sahre the same rendering engin **WebKit**.

Everthing in **HTML** is box, **Block-level** element expand to fill their container elements and force any subsequenct sibling eleent further down the page.
**Inline-element** do not expand to fill extra space and exist side-by-side next to inline neighbors.

**Rendering** is the process by which browsers after parsing the **HTML** and genrating the **DOM**, apply visual rules to the **DOM** contents and draw those pixels to the screen.

### CSS

**CSS*, Cascading Style Sheet, are used to style the visual presentation of **DOM** elements. It consist *selectors* and *properties*. Its also known as **CSS Rule**. The **Referencing Stlyes** are *embed*, *external* and *in-line*.

Later **CSS** rules override earlier ones and more specificity selector's rule will be applied.

```
selector0,
selector1 {
  property: value;
  property: value;
}
```

#### Type of Selector

**Type Selector**, selector match **DOM** elements name. `p` or `div`

**Descendant Selector**, match elements that are comtained by another element. `h1 em` or `div p`

**Class Selector**, match elements have been assigned specific class. `.className` or `.className0.className1`

**ID Selector**, match element with a given ID. `#idName`

### JavaScript

**JavaScript**, a scirpting language that can make pages dynamic by manipulating **DOM**. It is *loosely typed language.

Valid **JSON** indicer need to be surrounded by , `"`, double quote.
**GeoJSON** is a formalization of existing JavaScript object syntax. It's optimized for storing geodata.

#### JavaScript Gotchas

**Dynamic Typing**, the variable type is based on the value stored inside. Use `typeof` operator to check the variable type.

**Variable Hoisting**, variable declarations are hoisted up to the top of the function context.

**Function-level Scope**, variables are accessible anywhere within the *function* in which they reside.

**Global Namespace**, declear vairbale in global namespace will pollute it. Two(2) solutions are ONLY use variable in function, or create a global object and store variables inside that global object.

### SVG

**MDN** **SVG** In HTML Introduction is [here](https://developer.mozilla.org/en/docs/SVG_In_HTML_Introduction). It is **XML-based** elements taht don't have a closing tag **MUST** be self-closing. **SVG** is concepually similar to **HTML** `canvas`.

`pixel` or `px` is the default measurement unit. (Always specified  `px` explicitly)

SVG element reference is [here](https://developer.mozilla.org/en-US/docs/Web/SVG/Element) and SVG attribute reference is [here](https://developer.mozilla.org/en-US/docs/Web/SVG/Element).

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

Putting **SVG** styling into a **CSS** stlye. Put element selector `svg` to help developer remember which rules are SVG-specific.

```
SVG .rectangle0 {
  ...
}
```

There is no layers in **SVG** and **CSS** `z-index` is NOT supported either, the code sequence determin the drawing order.

Two(2) ways to set transparency, first is to use `RGBA()`, second is to use `opacity`. When both stlyes are in use, the result is multiplied.

# Setup

```
<script src="/javascripts/d3.min.js" type="text/javascript" charset="utf-8" async defer></script>
```

# Data

# Drawing with Data

# Scales

# Axes

# Update, Transitions, and Motion


***

# Legacy Note

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