# JavaScript Introduction

In this lab we will continue exploring JavaScript with examples and exercises.


## JavaScript Can Change and Create HTML Content / Styles / Hide or Show Elements

### 1. JavaScript Can Change HTML Content

The JavaScript methods getElementById() "finds" an HTML element (with id="demo") and creates the element content (innerHTML).

```JS
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript in Body</h2>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = "My First JavaScript";
</script>

</body>
</html> 
```

JavaScript can also change element contents. In this example, the JavaScript methods getElementById() "finds" an HTML element (with id="demo") and changes the element content (innerHTML) from "JavaScript can change HTML content" to "Hello JavaScript"

```JS
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p id="demo">JavaScript can change HTML content.</p>

<button type="button" onclick='document.getElementById("demo").innerHTML = "Hello JavaScript!"'>Click Me!</button>

</body>
</html>
```

### Exercises

1. Modify the last example and change the element content (innerHTML) to "Hi my name is (*your name*)"

### 2. JavaScript Can Change HTML Styles

In this example JavaScript changes the style of a text using the fontsize attribute:

```JS
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p id="demo">JavaScript can change the style of an HTML element.</p>

<button type="button" onclick="document.getElementById('demo').style.fontSize='35px'">Click Me!</button>

</body>
</html> 
```

### Exercises

1. Change the font colour to red.
2. Change the font to bold.

### 3. JavaScript Can Hide or Show HTML Elements

JavaScript can hide or show HTML elements by changing the display style. Let's hide the HTML element with id="demo":

```JS
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p id="demo">JavaScript can hide HTML elements.</p>

<button type="button" onclick="document.getElementById('demo').style.display='none'">Click Me!</button>

</body>
</html> 
```

Now, the element with id="demo" is hidden:

```JS
<p id="demo" style="display:none">Hello JavaScript!</p>
```

Let's use JavaScript to show it:

```JS
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p>JavaScript can show hidden HTML elements.</p>

<p id="demo" style="display:none">Hello JavaScript!</p>

<button type="button" onclick="document.getElementById('demo').style.display='block'">Click Me!</button>

</body>
</html> 
```

### Tutorials

## Set up the HTML

### 1. Create a new project

- Create a new folder
- Open it in Atom
- Add an img folder and put the images in
- Create an index.html file, and fill in the boiler plate html (type html and hit tab)
- Open index.html in Chrome

### 2. Create the HTML components

You will need a few things in your HTML

- A `<div>` with an id to display the score
- A `<div>` with an id to display the remaining time
- An `<img>` element for each of the two animals
- A `<div>` to act as the gameover screen.
  - This should include a `<h1>` that says Game Over.
  - It should also have a `<p>` with an id that you'll update to show the end score

### 3. Style your components

- Make the text of the score and time displays larger
- The animals need to each be 100% width. They also need to be hidden to start with. Use `display: none` to do this.
- The game over screen needs to:
  - be positioned at the top of the screen, in front of everything else.
  - be the size of the screen
  - have a solid background colour
  - be hidden to start with

## Randomly show an animal

### 1. Create a timeout

In JavaScript, you can make something happen after a delay using `setTimeout`. This function needs to know two things:

1. What to do after the delay - you give it the name of a function to run
2. How long the delay should be - this is in milliseconds.

For example, the following code will run a function called `doThis` after a delay of 1000ms, or 1 second.

```JS
setTimeout(doThis, 1000);
```

For now, have the delay be 1 second.

### 2. Create a function to show an animal

Create a new function, one that will be run by the `setTimeout` you just created. You'll need to create this above the `setTimeout` command.

To make sure things are working to this point, just put a `console.log` in there.

```JS
showAnimal = () => {
  console.log("Working");
}
```

Open up the developer tools in Chrome, go to the console tab, and refresh your page to make sure the function is being run after 1 second.

If it's working, remove the log line, and put a line in to show one of the animals.

You can do this by getting a reference to it and setting its `style.display` property to `block`.

### 3. Pick a random animal

We want to randomise the animal selected to display.

We can do this in JavaScript through a two step process:

1. Generate a random number between 0 and 1
2. See if the number is greater than 0.5.

This will create a 50% chance that something will happen.

We can generate a random number in JavaScript using the Math object. Its `random()` method will generate a random number between 0 and 1. So that's handy.

```JS
let randomNumber = Math.random();
```

In order to use this to decide whether to do something, we need to use an `if` statement. We'll get into `if` statements more in the coming weeks, but in short they let you check on a condition, and do something if it's true.

```JS
if(randomNumber > 0.5){
  // Show the mole
}
```

We can also have it do something if the condition is false, by following on with `else`:

```JS
if(randomNumber > 0.5){
  // show the mole
} else {
  // show the hedgehog
}
```

By this point, you should be able to refresh the page in Chrome, and after a second either the mole or the hedgehog will appear and stay there.

### 4. Hide the animal again

We don't want the animal to stay there forever, we want to hide them again after a short time. 500ms for instance.

To do this, we need to modify what's in that `if` statement a little. As well as showing an animal, we also need to set a timer that will run a function to hide the animal after 500ms.

You can use `setTimeout` again for this, one for each animal. This means you'll need two more functions, one to hide each animal by setting its `style.display` property back to `none`;

By this point, you should be able to:

1. Refresh the page in Chrome
2. After 1s one of the two animals appears
3. After another half a second, it disappears again

### 5. Show another animal

We want to create a stream of random animals, so that every second the user is shown a random animal, which stays on the screen for 500ms before disappearing again.

To do this, use `setTimeout` right at the end of function that shows an animal, after the `if` statement you've just created.

This `setTimeout` will need to call the function that it's in (this one that shows an animal) after one second. Just like the one you created to start things off in the first place.

By this point, a new random animal should show in the browser every second.

## Keeping score

The user should get a point if they click on the mole, and lose a point if they click on the hedgehog.

### 1. Create a variable to keep track of the score

At the top of your JavaScript create a variable called score that will start off with a value of 0.

### 2. Add event listeners to each animal

We need to detect a click on each of the animals. Add an event listener to each animal that will each run their own function.

### 3. Create the functions

You'll have one function that's run when the player clicks the mole, and one that's run when they click the hedgehog.

Make sure to create these above the lines that add event listeners.

Each of these functions will do two things:

1. Update the score variable by either adding 1 or subtracting 1.
2. Update the score display for the user

To change the text of an element on the screen, you need to do two things:

1. Get a reference to the element
2. Change the value of its `textContent` property

You can do both of these things in one go:

```JS
document.getElementById('scoreDisplay').textContent = "Score: " + score;
```

Test this works - the display should update as you click the animals.

**Note: This doesn't work so well when you've got mobile mode turned on in the Chrome dev tools.**

## Create a countdown

So far you've used `setTimout` to be able to do something after a one-shot delay. However, we can also have some code repeated at intervals using `setInterval`.

### 1. Create a variable

As with the score, we need a variable to keep track of how much time is left. Create it at the top of your JavaScript underneath the line where you create the score variable.

```JS
let timeRemaining = 30;
```

### 2. Create a timer

At the bottom of your JavaScript, use `setInterval` to run a function every second.

```JS
setInterval(updateCountdown, 1000);
```

### 3. Create the timer function

Create the function above the `setInterval` line in your code. Use `console.log` to make sure it's working.

### 4. Update the time remaining

Make the function you just created do two things:

1. Subtract 1 off the time remaining variable
2. Update the time remaining display for the user

You should be able to refresh your browser and see the time counting down.

## Stop the game when the time runs out

There are two things that need to happen when the time runs out:

1. The countdown timer should stop
2. We update and show the game over screen

### 1. Stop the timer

In order to stop a timer created with `setInterval` we need to be able to refer to it. We can do this by storing a reference to it in a variable when we create it. Update your code to something like this:

```JS
let countdownTimer = setInterval(updateCountdown, 1000);
```

In the function that this timer runs, we need to check the value of the remaining time, and stop the timer when it reaches 0.

We can do this using an `if` statement.

```JS
if(timeRemaining == 0){
  clearInterval(countdownTimer);
  // update and show the game over screen
}
```

Notice the double == above. This is easy to get wrong. If we are comparing two values to see if they are equal, we use a double ==. A single = will assign the value of the right-hand side to whatever's on the left-hand side, and that's not what we want to do here.

### 2. Update and show the game over screen

There are two steps here - update and show.

We want to tell the player what their final score is. You put a `<p>` in the game over `<div>` to do just this, so get a reference to it and use its `textContent` property to tell the user their score.

To show the game over screen, get a reference to it and set its `style.display` property to `block`.

Test things out - you might want to set `timeRemaining` to a small starting value to test this, rather than wait 30s every time you want to see if it works.

## Going Further

There are a couple of things you can do to take this a litte further.

### Stop showing animals

Although the game over screen is covering things up, animals are still being randomly selected and shown behind it. It's a little sloppy to leave this running.

One way to stop it when the game ends is to create a boolean variable that keeps track of whether the game is running or not, set to true initially.

```JS
let playing = true;
```

In your function that shows a new animal you have the line that uses `setTimout` to show another animal after 1s. Wrap this in an `if` statement that will only run it if playing is true.

When the time runs out, set that playing variable to false.

### Randomise the time gap between animals

This can make the game a little more tense. Let's say we want to have a delay between 500ms and 2s, rather than the fixed animal every second that we've currently got.

To do this, we'll need to randomly generate the value for the delay that `setTimout` uses.

We've already seen how to create a random number between 0 and 1, but we want a random number between 500 and 2000.

This is a range of 1500, starting at 500. We can modify what we get from `Math.random()` to achieve this by multiplying by the range and then adding the start value:

```JS
let randomDelay = Math.random() * 1500 + 500;
```

You can then use this in `setTimeout` as the delay length.
