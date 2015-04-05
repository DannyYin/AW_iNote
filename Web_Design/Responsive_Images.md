# Responsive Images

## Getting Up and Running

### Why Responsive Images?

The goal is to produce the **highest** quality images with the **fewest bytes** possible.
It is more like **Art** but **Science**.

> Images consume more than 60% of the bytes that croess the web.

**NOTE**: Most of the bytes cross the web are for video.

> Create a product, don't re-imagine one for small screens. Greate mobile products are created, never ported.
>
> -- <cite>Brian Fling</cite>

### Introducing Remote Debuging

[Remote Debugging on Android with Chrome](https://developer.chrome.com/devtools/docs/remote-debugging)

**Addtional Note for Chrome Canary**: 

Chrome Canary is the developer version of Chrome.
It looks and acts like the regular Chrome browser, but it includes new and experimental features that haven't been released yet.
It is recommended analyzing websites with Canary to take advantage of the latest tech. 

[iOS Webkit Debug Proxy](https://github.com/google/ios-webkit-debug-proxy)

## Units, Formats, Environments

### Units

Images can be different due to compression level (same display size different file size) and auctual (natural) resolution.

<var>Total Bits</var> = <var>pixels</var> x <var>Bits Per Pixel</var>

NOTE: `max-width=100%` sometime is a good for display good image for different screen size.
Moreover, using `width: calc((100%-10px)/2);` which alows you do some simple calculation with css values.
It is a great way to combine absolute and relative values.
Pseudo class selectors are also helpful in certain situation, `img:last-of-type {margin-right: 0;}`.

For more about `calc` click [here](https://developer.mozilla.org/en-US/docs/Web/CSS/calc).

### Orientation

Never assume view-port sizes are the same. 

Introducing `vh` for *view-port height* and `vw` for *view-port width*.
1 `vh` unit -> 1% of view-port height.

```css
width: 100vmax;
height: 100vmax;
/* make element cover the whole view-port */
```

### Raster and Vector

Raster -> HTML Canvas Element

Vector -> SVG, Scales without quality degradation

### Image Optimisation Environment

Tools for image optimisation environment are **Grunt**, **ImageOptim** (GUI Tool for Mac ONLY), and **ImageMagick**.

### Image Compression

[PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)

### Introducing <figure>

The HTML `<figure>` Element represents self-contained content, frequently with a caption (`<figcaption>`), and is typically referenced as a single unit.

Continue [HERE](https://www.udacity.com/course/viewer#!/c-ud882/l-3520939843/m-3478679768)

## Images with Markup

## Full Responsiveness

