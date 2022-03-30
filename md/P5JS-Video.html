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

For example, we can remove one of the colour components of the pixels
  
  
  
  
Next, we'll skip ahead to a sketch that's a little more exciting. Modify the last example to try this:

````JS
function setup() {
  // The createCanvas() function creates an HTML canvas on the web page
  let cnv = createCanvas(800, 400);
  // The canvas position
  cnv.position(10, 60);
}

// The draw() function is automatically called after the setup() function.
// The draw() loop infinitely runs the code block inside the function from top to bottom.
function draw() {
  // The background() function sets the background color of the p5.js canvas.
  background(60, 60, 140);
  
  if (mouseIsPressed) {
    // This draws an ellipse, with its center 50 pixels over from the left and 50 pixels down from the top, with a width and height of 80 pixels.
    ellipse(mouseX,mouseY,80,80);
  }
}
````

As you can see, it is straightforward to use mouse data in p5.js.

The variables `mouseX` and `mouseY` (note the capital X and Y) store the x-coordinate and y-coordinate of the cursor relative to the origin in the upper-left corner of the display window. `mouseIsPressed` detects if the mouse has been pressed.

**Exercise 4**
Move the function `background(60, 60, 140)` from draw() to setup() and study the differences.

**Exercise 5**
Investigate how to use the function random() (<https://p5js.org/reference/#/p5/random>) to change the width and height of each circle between 20 and 80.

**Exercise 6**
Investigate how to use the function random() (<https://p5js.org/reference/#/p5/random>) to change the colour of each circle.


## The draw() function

The draw() function is automatically called after the setup() function, which runs once at the program’s start. The draw() loop infinitely runs the code block inside the function from top to bottom.

p5.js automatically runs the program at 60 frames per second. This means that the draw() function runs repeatedly 60 times per second. You can change the number of frames shown per second by using the `frameRate()` function.

To keep track of the number of frames rendered, p5.js provides a built-in variable called `frameCount`.

Let's see in this example how to animate a circle using these concepts.

````JS
let x = 0;

function setup() {
  let cnv = createCanvas(800, 400);
  cnv.position(10, 60);
  
  // frameRate() changes the number of frames shown per second
  frameRate(10);
}

// The draw() loop infinitely runs the code block inside the function from top to bottom.
function draw() {
  background(60, 60, 140);
  circle(x,40,50);
  x = x + 1;
}
````

**Exercise 7**
Change the number of frames per second to 80.

**Exercise 8**
Investigate how to 'reset' the position of the circle when it reaches the end of the canvas. (Save this exercise, you will need it in Exercise 9).

## Adding 'noise' to animations

There may be times when you want to create random movements that are more natural. p5.js has a noise() (<https://p5js.org/reference/#/p5/noise>) function that does exactly this!

Let's see in this example, how to animate a circle using the `noise()` function.

````JS
let xoff = 0.0;

function setup() {
  let cnv = createCanvas(800, 400);
  cnv.position(10, 60);
  
  // frameRate() changes the number of frames shown per second
  frameRate(10);
}

// The draw() loop infinitely runs the code block inside the function from top to bottom.
function draw() {
  background(60, 60, 140);
  xoff = xoff + 0.01;
  let n = noise(xoff) * width;
  
  circle(n,40,50);
}
````

**Exercise 9**
Use 'noise()' to create a 'shaking movement' to the circle of Exercise 8 .  

**Exercise 10 (more difficult!)**
Use a 'for loop' command to create 10 animated circles without overlap. You program must include the following:

- Each circle must have a random colour (same colour during all the animation).
- Each circle has to move at different velocities from left to right.
- Each circle must include a 'shaking movement'.
- Each circle must 'restart' its possition when it reaches the end of the canvas.

<br><br>
# Review: audio with p5.js

## Load and Play audio with p5.js

p5.sound extends p5 with Web Audio functionality including audio input, playback, analysis and synthesis.

<https://p5js.org/reference/#/libraries/p5.sound>

Let's see an example of how to load and play a sound file using p5.sound.

This is the HTML template we are going to use

````JS
<!DOCTYPE html>
<html lang="">

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>p5.js example</title>
  <style>
    body {
      padding: 0;
      margin: 0;
    }
  </style>
  <script src="../libraries/p5.js"></script>
  <script src="../libraries/p5.sound.min.js"></script>
  <script src="sketch.js"></script>
</head>

<body>
  <main>
  </main>
</body>

</html>
````

And this is the Javascript file

````JS
let mySound;
var playStopButton;

function preload() {
  soundFormats('wav', 'mp3');
  mySound = loadSound('/sounds/war-of-worlds2');
}

function setup() {
  createCanvas(400, 200);
  background(180);
    
  playStopButton = createButton('play');
  playStopButton.position(200, 20);
  playStopButton.mousePressed(playStopSound);
}

function draw() { 
}

function playStopSound() {
  if (mySound.isPlaying())
    {
      mySound.stop();
      //mySound.pause();
      playStopButton.html('play');
    } else {
      //mySound.play();
      mySound.loop()            
      playStopButton.html('stop');
    }  
}
````

Let's add a slider to control the volume of the audio. This is the new Javascript file.

````JS
let mySound;
var playStopButton;
var sliderVolume;

function preload() {
  soundFormats('wav', 'mp3');
  mySound = loadSound('/sounds/war-of-worlds2');
}

function setup() {
  createCanvas(400, 200);
  background(180);
    
  playStopButton = createButton('play');
  playStopButton.position(200, 20);
  playStopButton.mousePressed(playStopSound);

  sliderVolume = createSlider(0, 1.5, 1, 0.01);
  sliderVolume.position(20,25);
  text('volume', 80,20);
}

function draw() { 
  mySound.setVolume(sliderVolume.value());
}

function playStopSound() {
  if (mySound.isPlaying())
    {
      mySound.stop();
      //mySound.pause();
      playStopButton.html('play');
    } else {
      //mySound.play();
      mySound.loop()            
      playStopButton.html('stop');
    }  
}
````

## Exercise 1
Explore how to improve the previous program by adding a 'rate' and 'pan' sliders.

## Exercise 2
Explore how to add one or several effects to your program. For example, a delay (<https://p5js.org/reference/#/p5.Delay>) or a filter (<https://p5js.org/reference/#/p5.Filter>)

## Exercise 3 (Optional)
Explore how to add a 'jump' button to your program. 

## Interaction

p5.js provides several tools for interaction. Let's study the following code. In this example, the size of a circle changes with the sound amplitude.

````JS
var mySound;
var playStopButton;
var jumpButton;
var sliderVolume;
var sliderRate;
var sliderPan;

var amplitude;

function preload() {
  soundFormats('wav', 'mp3');
  mySound = loadSound('/sounds/233709__x86cam__130bpm-32-beat-loop');
}

function setup() {
  createCanvas(400, 400);
  background(180);
    
  playStopButton = createButton('play');
  playStopButton.position(200, 20);
  playStopButton.mousePressed(playStopSound);
  jumpButton = createButton('jump');
  jumpButton.position(250, 20);
  jumpButton.mousePressed(jumpSong);

  sliderVolume = createSlider(0, 1, 1, 0.01);
  sliderVolume.position(20,25);
  text('volume', 80,20);
  sliderRate = createSlider(-2, 2, 1, 0.01);
  sliderRate.position(20,70);
  text('rate', 80,65);
  sliderPan = createSlider(-1, 1, 0, 0.01);
  sliderPan.position(20,115);
  text('pan', 80,110);
  
  amplitude = new p5.Amplitude(0);
}

function draw() {
  background(180);
  text('volume', 80,20);
  text('rate', 80,65);
  text('pan', 80,110); 
  
  let vol = Math.pow(sliderVolume.value(), 3); 
  mySound.setVolume(vol);
  mySound.rate(sliderRate.value());
  mySound.pan(sliderPan.value());
  
  let level = amplitude.getLevel();
  let diameter = map(level, 0, 1, 0, 200);
  console.log(level);
  
  fill(0);
  circle(250, 250, diameter);
}

function jumpSong() {
  var dur = mySound.duration();
  var t = random(dur);
  mySound.jump(t);
}

function playStopSound() {
  if (mySound.isPlaying())
    {
      mySound.stop();
      //mySound.pause();
      playStopButton.html('play');
    } else {
      //mySound.play();
      mySound.loop()            
      playStopButton.html('stop');
    }  
}
````

## Exercise 4
Improve the previous program, so the colour of the circle also changes with the sound amplitude

## Capturing and recording audio with p5.js

To capture and record audio using p5.js is also straightforward. Let's study the following example.

````JS
let mic;
let recorder;
let soundFile;
let state = 0;

function setup() {
  createCanvas(400, 400);
  background(200);
  text('Click to record', 40, 40);
  
  // Create an Audio input
  mic = new p5.AudioIn();
    
  // start the Audio Input.
  // By default, it does not .connect() (to the computer speakers)
  mic.start();
  
  // create a sound recorder
  recorder = new p5.SoundRecorder();
  // connect the mic to the recorder
  recorder.setInput(mic);
  // this sound file will be used to playback & save the recording
  soundFile = new p5.SoundFile();
}

function draw() {  
  // Get the overall volume (between 0 and 1.0)
  let vol = mic.getLevel();
}

function mouseClicked(){
  // ensure audio is enabled
  if (getAudioContext().state !== 'running') {
     getAudioContext().resume();
  }
  
  // make sure user enabled the mic
  if (state === 0 && mic.enabled) {
    background(255,0,0);
    text('Recording', 40, 40);    
    
    // record to our p5.SoundFile
    recorder.record(soundFile);
    state++;
  }
  else if (state === 1) {  
    background(0,255,0);
    text('Click to play and download!', 40, 40);
    
    // stop recorder
    recorder.stop();
    state++;
  }
  else if (state === 2) {
    background(200);
    text('Click to record', 40, 40);
    
    // play the result
    soundFile.play();
    
    // save the soundFile
    save(soundFile, 'output.wav');
    state = 0;
  }
}
````

## Exercise 5
Make a recording, download the file and open it in an audio editor (Audition, for example).

## Exercise 6
Modify the following code, so that the program also draws an ellipse with height based on volume.
