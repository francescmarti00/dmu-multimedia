# SVGs and Animation

Scalable Vector Graphics are well suited to a wide range of graphic uses and are easy to animate in detail.

<iframe src="https://dmureplay.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=fc4898dc-f088-4e18-b8c2-acbd0136a2db&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all" height="405" width="720" style="border: 1px solid #464646;" allowfullscreen allow="autoplay"></iframe>

## What is an SVG?

### Scalable Vector Graphic

Vector - comprised of numbers representing paths and fills - not pixels. They are mathematical representations of images.

## Why SVG?

- Crisp on any device size / resolution
- Supported in all modern browsers
- Fairly easy to make and edit
- Can manipulate with CSS and JS

## SVGs are XML

XML = Extensible Markup Language  
HTML is based on this  
It means elements are made of tags

## Creating an SVG

To create an SVG we use the `<svg>` object. Here is an example of a simple SVG circle into an HTML page:

```html
<!DOCTYPE html>
<html>
<body>

<h1>This is a SVG circle</h1>

<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
</svg>

</body>
</html>
```

Code explanation:

- An SVG image begins with an `<svg>` element.

- The width and height attributes of the `<svg>` element define the width and height of the SVG image.

- The `<circle>` element is used to draw a circle.

- The cx and cy attributes define the x and y coordinates of the center of the circle. If cx and cy are not set, the circle's center is set to (0, 0).

- The r attribute defines the radius of the circle.

- The stroke and stroke-width attributes control how the outline of a shape appears. We set the outline of the circle to a 4px green "border".

- The fill attribute refers to the color inside the circle. We set the fill color to yellow.

- The closing `</svg>` tag closes the SVG image.

You can see a list of redefined shape elements in <https://www.w3schools.com/graphics/svg_rect.asp>  
  
## ViewBox?

```html
<svg width="200" height="200" viewBox="0 0 200 200"></svg>
```

This is like the viewport of SVG element, defining its internal geometry.  
It is the window through which we view the SVG.  
The four numbers represent the top left x and y, and the width and height.  
The viewbox can then be scaled using the width and height attributes of the svg object.
  
As we can see, in this example, viewBox doesn't change the result. If we remove the viewBox attribute we get the same image

```html
<!DOCTYPE html>
<html>
<body>

<h1>My is a SVG circle</h1>

<svg width="200" height="200" viewBox="0 0 200 200">
  <circle cx="50" cy="50" r="40" fill="blue" />
</svg>

</body>
</html>
```
  
To move the circle 100px to the right we should write

```html
<svg width="200" height="200" viewBox="-100 0 200 200">
```

To move the circle 100px down, we should write  

```html
<svg width="200" height="200" viewBox="0 -100 200 200">
```
  
This code decreases the size of the circle

```html
<svg width="200" height="200" viewBox="0 0 400 400">
```
  
Here is an example of a simple SVG circle into an HTML page:

## Some SVG Elements

### Shapes

There are four basic shapes. In each case, we use attributes to describe their geometric properties, such as their location within the viewbox.

```html
<rect x="10" y="10" width="180" height="180" fill="red" />
<circle cx="300" cy="100" r="90" fill="blue" />
<ellipse cx="100" cy="300" rx="90" ry="50" fill="green" />
<polygon points="210,210 390,390 390,210 210,390" fill="yellow" />
```

### Gradients

We can define a gradient using either the `<linearGradient>` or `<radialGradient>` objects.

```html
<linearGradient id="linGradient" gradientTransform="rotate(90)">
  <stop offset="5%" stop-color="gold" />
  <stop offset="95%" stop-color="red" />
</linearGradient>
```

```html
<RadialGradient id="radGradient">
  <stop offset="5%" stop-color="gold" />
  <stop offset="95%" stop-color="red" />
</RadialGradient>
```

We then apply a gradient to a shape using the shape's `fill` attribute.

```html
<circle cx="5" cy="5" r="4" fill="url('#linGradient')" />
```

### Filters

Use a `<filter>` element to composite a number of filter effects.

```html
<filter id="blurFilter">
  <feGaussianBlur stdDeviation="5" />
</filter>
```

Filters include blur, lighting, drop shadow, distortion and more (<https://www.w3schools.com/graphics/svg_filters_intro.asp>).

This `<filter>` element is then applied to an object using its `filter` attribute.

```html
<circle cx="170" cy="60" r="50" fill="green"
          filter="url(#blurFilter)" />
```

## Animation

There are several methods available.

### Using CSS

You can use CSS transitions and @keyframe animations (see, for example, <https://www.w3schools.com/cssref/css3_pr_animation-keyframes.asp>).

Just give your SVG shapes class names or ids to select them with CSS and animate them as you would any other element.

### Using Greensock

Greensock can animate SVG elements as normal, including attributes like `fill`.

Note: Greensock can also animate object properties, which can be useful for animating the points of a polygon or path.

### Using the SVG `animate` element

You can nest an `<animate>` element inside the shape you want to animate.

```html
<ellipse cx="100" cy="100" rx="90" ry="50" fill="green">
  <animate
    attributeName="rx"
    values="90;50;90"
    dur="1s"
    repeatCount="indefinite"
  />
  <animate
    attributeName="ry"
    values="50;90;50"
    dur="1s"
    repeatCount="indefinite"
  />
</ellipse>
```

You can animate attributes of filters and gradients too.
  <https://www.w3schools.com/css/css3_animations.asp>

## Some SVG Help

There are third-party libraries for working with SVGs.

Snap.svg <http://snapsvg.io>  
SVG.js <https://svgjs.com/docs/3.0/>  
SVGO <https://jakearchibald.github.io/svgomg/>

## Further Resources

<div style='text-align: left'>

Sarah Drasner (2017) SVG Animations: From common UX implementations to complex responsive animation  
Jake Giltsoff (n.d.) SVG On The Web - A Practical Guide <https://svgontheweb.com>  
Chris Coyier (2017) Animating SVG with CSS <https://css-tricks.com/animating-svg-css/>  
Mozilla (n.d.) MDN Reference on SVG <https://developer.mozilla.org/en-US/docs/Web/SVG>

</div>
