# HTML5 Canvas

## HTML5 Canvas Basic

Canvas is a powerful **API**, it can be used to resize, change images, do animation and interaction.

`<canvas>` is a 2D surface that takes instruction and immediately render it.

### Createing a Canvas

```HTML
<canvas id="c" width="200" height="200"></canvas>
```

```JavaScript
var c = document.querySelector("#c");
var ctx = c.getContext("2d");
```

### Coordinate System

Its not **Geometry Class** so the **Cartesion Coordinates System** is not been used here. Canvas system's (0, 0) is on the top left.

### Loading Images Code

```HTML
<canvas id="c" width="200" height="200"></canvas>
<!-- <img src="http://website.com/img.jpg"> -->
```

```JavaScript
var c = document.querySelector("#c");
var ctx = c.getContext("2d");

var image = new Image();
image.src = "imageName.jpg";
image.onload = function(){
  console.log("Loaded image");
  ctx.drawImage(image, 0, 0, c.width, c.height);

  // In order to save the image use code below
  var savedImage = c.toDataURL();
  window.open(savedImage);

  // Draw image
  ctx.fillRect(100, 100, 100, 100);
  ctx.fillRect(50, 50, 50, 50);

  // var savedImage = c.toDataURL();
  // window.open(savedImage);
  ctx.fillStyle = "blue";
  ctx.fillRect(100, 100, 100, 100);
  ctx.clearRect(100,100, 50, 50);
  ctx.strokeRect(50, 50, 50, 50);

  // Drawing Path
  ctx.beginPath();
  ctx.moveTo(10, 10);
  ctx.lineTo(50, 50);
  ctx.lineTo(50, 10);
  ctx.lineTo(10, 10);
  // ctx.fill();    <--- To fill the shape
  ctx.stroke();   //<--- To stroke the shape
}
```

NOTE: The simplest way is to use `SimpleHTTPServer`. Go to the target directory and use `python -m SimpleHTTPServer`. In order to avoid some security issues.

### Moving Objects in Canvas

Canvas2D allows you to translate, rotate or scale objects.

`scale(x, y)` multiplies the x and y value by a given factor. `ctx.scale(2, 3)` makes 2x large on the x axis and 3x large on the y axis.

`translate(x, y)` moves subsequent draw commands by x pixels on horizontally and y pixels on vertically.

`ctx.rotate(angleRadians)` rotates an object a certain number of radians about its center. (radians = degree * Math.PI/180)

NOTE: Order of operations should scale object first, rotate next, then finally translate.

### Introducing 'save()' and 'restore()'

Every canvas object contains a stack of drawing states.
Stacks are data structures that only let you push new item at one end.
When you retrieve an item, its the last item that was pushed or Last In-First Out (LIFO).

Draw a couple rectangles in different colors. One solution is reassigning the `fillStyle` each time instead of using `save` and `restore`.

```JavaScript
var c = document.querySelector("#c");
var ctx = c.getContext("2d");

ctx.fillStyle = 'blue';
ctx.fillRect(0, 0, 50, 50);

ctx.fillStyle = 'green';
ctx.fillRect(100, 100, 10, 10);

ctx.fillStyle = 'blue';
ctx.fillRect(200, 10, 20, 20);

// Better way
ctx.fillStyle = 'blue';
ctx.fillRect(0, 0, 50, 50);

// Save state with blue fill
ctx.save();
ctx.fillStyle = 'green';
ctx.fillRect(100, 100, 10, 10);
// Restore to blue fill
ctx.restore();
ctx.fillRect(200, 10, 20, 20);
```

NOTE: The canvas state can store the following things.

- Current transformation matrix (rotation, scaling, translation)
- `strokeStyle`
- `fillStype`
- `font`
- `globalAlpha`
- `lineWidth`
- `lineCap`
- `lineJoin`
- `miterLimit`
- `shadowOffsetX`
- `shdowOffsetY`
- `shadowBlur`
- `shadowColor`
- `globalCompositeOperation`
- `textBaseline`
- Current clipping region

### Colors

Colors can be one of the 140 or so names declared by the **CSS Specification** or a **RGB** hexidecimal code.

### Drawing Text

```HTML
ctx.strokeText("Text Sample", 50, 10);
ctx.fillText("Text Sample", 50, 10);

// Sample
ctx.font = 'bold 39px Impact';
ctx.textAlign = 'center';
ctx.fillStyle = 'white';
ctx.strokeStyle = 'black';
ctx.lineWidth = 3;
ctx.strokeText("CANVAS MEMES!!!", c.width/2, 50);
```

## From Pixels to Animation

### What's a Pixel

Red, Green, Blue, Alpha (Solid or Transparent).

### Filters and Effects

The grayscale and invert color effects can be created using **Canvas** code.

### Canvas 2D Image Data

Images data contains width, height, data (Uint8ClampedArray).

`createImageData` initialise blank image data.

`getImageData` retrive data to the canvas

`putImageData` store data to the canvas

**Data Sample**

```JavaScript
[[r, g, b,a], [r, g, b, a]...[r, g, b, a]]
[r, g, b, a, r, g, b, a, r, g, b, a, r, g, b, a]
```

```JavaScript
var c = document.querySelector('#c');
var ctx = c.getContext('2d');
var data = ctx.getImageData(0, 0, 500, 500);

function paintGreen(imageData){
  var numPixels = imageData.data.length / 4;
  for (var i = 0; i < numPixels; i++) {
    if (i % 10 === 0) {
      imageData.data[i * 4 + 1] = 255;
      imageData.data[i * 4 + 3] = 255;
    }
  }
  ctx.putImageData(imageData, 0, 0);
}

paintGreen(data);
```

### Playing Videos with Canvas

Play a video using `requestAnimationFrame` is just one of the many interactive things.

Processing keyboard input, can use open source projects libray like [Kibo](https://github.com/marquete/kibo). Kibo allows reference keys by their common names instead of keycodes.

Processing mouse input, the mouse can accept `click` and `mousedown` events.
However, we have to do a little work to figure out where exactly in the canvas the user has clicked. Mouse click events return `clientX` and `clientY` positions that are global to the browser window.
Every element knows where it is positioned relative to the browsers (0, 0) position (`offsetLeft` and `offsetTop`).

NOTE: To get the canvas-relative of click, you need to subtract the `offsetLeft` and `offsetTop` values from `clientX` and `clientY`.

```JavaScript
// example code from mr doob : http://mrdoob.com/lab/javascript/requestanimationframe/
var canvas, context;
init();
animate();
function init() {
    canvas = getCanvas();
    context = canvas.getContext( '2d' );
}
function animate() {
    requestAnimationFrame( animate );
    draw();
}
function draw() {
    var time = new Date().getTime() * 0.002;
    var x = Math.sin( time ) * 96 + 38;
    var y = Math.cos( time * 0.9 ) * 96 + 38;

    context.fillStyle = 'rgb(245,245,245)';
    context.fillRect( 0, 0, 255, 255 );
    context.fillStyle = 'rgb(255,0,0)';
    context.beginPath();
    context.arc( x, y, 10, 0, Math.PI * 2, true );
    context.closePath();
    context.fill();
}
```