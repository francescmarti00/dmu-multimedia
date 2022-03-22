# Audio in the browser with p5.js

In this lab we are going to introduce p5.js.
p5.js is a JavaScript library for creative coding, with a focus on making coding accessible and inclusive for artists, designers, educators, beginners, etc.

Here are some useful links:

p5.js webpage: <https://p5js.org/><br>
Get started: <https://p5js.org/get-started/><br>
Some (amazing) exemples: <https://openprocessing.org/browse/>

## p5.sound, a p5.js library for working with audio in the browser

p5.sound extends p5 with Web Audio functionality including audio input, playback, analysis and synthesis.

<https://p5js.org/reference/#/libraries/p5.sound>

## Load and Play audio wigh p5.js

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

## Exercise 4: Improve the previous program, so the colour of the circle also changes with the sound amplitude

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
