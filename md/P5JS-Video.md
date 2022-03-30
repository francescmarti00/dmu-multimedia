# Working with video with p5.js

## Loading and displaying video with p5.js.

The p5.js library makes it easy to load, display and control video playback from your sketch. Let’s see an example.

As always, we are going to use two files, an HTML file and a Javascript file. Remember to run the examples on localhost, to avoid problems. 

This is the 'empty' HTML file

```HTML
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>p5.js video</title>
  <script src="https://cdn.jsdelivr.net/npm/p5@1.4.1/lib/p5.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/p5@1.4.1/lib/addons/p5.sound.js"></script>
  <script src="sketch.js"></script>
</head>

<body>
  <main>
  </main>
</body>

</html>
```

And this is the Javascript file

```JS
let vid;
let playing = false;

function setup() {
  createCanvas(0, 0);
  vid = createVideo("Commercial_1958.mp4");
}

function draw() {
}

function mousePressed() {
  if (!playing) {
    vid.play();
    // vid.loop();
    playing = true;
  }
  else {
    vid.pause();
    playing = false;
  }
}
```

## Video Capture

Capture video from the webcam and display on the canvas is also straightforward with p5.js.

Let's study this code

```JS
let capture;

function setup() {
  createCanvas(0, 0);
  capture = createCapture(VIDEO);
  capture.size(320, 240);
}

function draw() {
  background(255);
}
```

## Video filters

p5.js inclludes some filters, ready to use, such as INVERT.

```JS
let capture;

function setup() {
  createCanvas(320, 240);
  capture = createCapture(VIDEO);
  capture.size(320, 240);
  //capture.hide();
}

function draw() {
  background(255);
  image(capture, 0, 0, 320, 240);
  filter(INVERT);
}
```

**Exercise 1**
Investigate the function filter() (<https://p5js.org/reference/#/p5/filter>) and add the following filters to the captured image: THRESHOLD, GRAY, OPAQUE, INVERT, POSTERIZE, BLUR, ERODE and DILATE.

## Working with video pixels
  
```JS
let capture;

function setup() {
  createCanvas(320, 240);
  capture = createCapture(VIDEO);
  capture.size(320, 240);
  capture.hide();
}

function draw() {
  background(255);

  capture.loadPixels();
  for (let y=0; y<capture.height; y++) {
    for (let x=0; x<capture.width; x++) {
      let position = ((capture.width * y + x)*4);
      let r = capture.pixels[position];
      let g = capture.pixels[position+1];
      let b = capture.pixels[position+2];
    }
  }
  capture.updatePixels();
  
  image(capture, 0, 0, 320, 240);
}
```
  
## Pixel-to-pixel operations
  
The simplest image processing operations are those that transform each pixel in isolation, i.e. the transformation of a pixel does not depend on the surrounding pixels, it depends only on the value of the image f at the pixel (x,y). These operations are called pixel-to-pixel operations.

For example, we can remove one of the colour components of the pixels.

```JS
let capture;

function setup() {
  createCanvas(320, 240);
  capture = createCapture(VIDEO);
  capture.size(320, 240);
  capture.hide();
}

function draw() {
  background(255);

  capture.loadPixels();
  for (let y=0; y<capture.height; y++) {
    for (let x=0; x<capture.width; x++) {
      let position = ((capture.width * y + x)*4);
      let r = capture.pixels[position];
      let g = capture.pixels[position+1];
      let b = capture.pixels[position+2];
      
      capture.pixels[position] = 0;
    }
  }
  capture.updatePixels();
  
  image(capture, 0, 0, 320, 240);
}
```

**Exercise 2**
Repeat the previous program but removing the blue component of the pixels.

**Exercise 3**
Make a filter to brighten your webcam image.
  
**Exercise 4**
Make a filter to darken your webcam image.

**Exercise 5**
There are several methods to transform an RGB image to a grayscale image. For example:

The luminosity method: this is the method used in the aforementioned example. If you check the code, you can see that the formula that defines this transformation is

Grayscale = 0.2126*r + 0.7152*g + 0.0722*b

The weighted method: this method is defined by the formula

Grayscale = 0.299*r + 0.587*g + 0.114*b

The average method: this method takes the average value of R, G, and B as the grayscale value

Grayscale = r/3 + g/3 + b/3

Make a filter to transform an RGB image to a grayscale image using the luminosity method.

**Exercise 6**
Make a 'custom filter' combining pixel-to-pixel operations and the function filter().

## More advanced filters 

Study the following example.

```JS
/*
VIDEO PIXELS
Jeff Thompson | 2021 | jeffreythompson.org

Video input is basically just like an image!
We can get it's width and height, and access
the frame's pixel values too!

BASED ON
https://p5js.org/examples/dom-video-pixels.html

*/

let video;

function setup() {
  createCanvas(windowWidth, windowHeight);

  // webcam capture (at the size of the window)
  video = createCapture(VIDEO);
  video.size(width, height);
  video.hide();
}

function draw() { 
  background(255);

  // try experimenting with this
  let gridSize = int(map(mouseX, 0,width, 15,50));

  // the video has pixels just like an image!
  video.loadPixels();
  for (let y=0; y<video.height; y+=gridSize) {
    for (let x=0; x<video.width; x+=gridSize) {
      
      // at the current position, get the red
      // value (an approximation for brightness)
      // and use it to create the diameter
      let index = (y * video.width + x) * 4;
      let r = video.pixels[index];
      let dia = map(r, 0,255, gridSize,2);
      
      // draw a circle at the current location
      // using the diameter we calculated
      fill(0);
      noStroke();
      circle(x+gridSize/2,y+gridSize/2, dia);
    }
  } 
}
```

**Exercise 7**
Modify the previous code and fill the circles with the pixel color instead of black.
