# Responsive Web Design Fundamentals

## Why Responsive?

[Web Fundamentals](https://developers.google.com/web/fundamentals/?hl=en)

## Starting Small

Device Independent Pixels (DIP) <-> Hardware Pixels

Browser provide font-boosting but result is bad.

Setting the viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Recommand Practice for Media HTML Tags

```css
img,
embed,
object,
video {
	max-width: 100%;
}
```

On mobile device the tapable button size should NOT smaller than 48px.

```css
button {
	min-width: 48px;
	min-height: 48px;
}
```

### Mobile First

Priorities content from mobile to desktop and even TV, hence the key content is always there. Also code from small to large also good. The most important reason to start from small is **performance**, thinking performance from the beginning.

## Building Up

Introduce Design Pattern.

Media Query to change the style based on screen size. Most use properties are `min-width` and `min-height`.

**Type One Media Query**

```html
<link rel="stylesheet" href="style.css" media="screen and (min-width:500px)">
```

**Type Two Media Query**

```css
@media screen and (min-width: 500px)
{	
	body {
		background-color: black;
	}
}
```

**Breakpoint** is where page layout starting change. 

### How to find Breakpoint?

Use the content to find the best **Breakpoint**.

### Introduce Flexbox 

The Flexbox Layout (Flexible Box) module (currently a W3C Last Call Working Draft) aims at providing a more efficient way to lay out, align and distribute space among items in a container, even when their size is unknown and/or dynamic (thus the word "flex").

## Common Responsive Patterns

### Mostly Fluid

Similar to column drop but more like grid system. Using Media Query with breakout condition.

### Column Drop

Most easy way to implement is using flexbox.

### Layout Shifter

The order of box changes with different screen size.

### Off Canvas

Hide the content before meet certain condition, like, hamburger button clicked.

## Optimizations

### Word Optimization

65 CPL (Character Per Line) is good text measure for web.

### Major Breakpoint and Minor Breakpoint

Minor breakpoint change the font size and other minor appearance.
