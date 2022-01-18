# JavaScript Basics (part 4)

In this lab we will continue exploring JavaScript with examples and exercises.
</br> 

## The JavaScript addEventListener() method

We have seen several examples in which we call a JavaScript function using HTML events such as 'onclick', 'ondblclick', 'onmouseover', etc.  
For example, in this code, we change the position of a rentangle by clicking on it.

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title></title>
    <style>
      #square {
        background: green;
        width: 100px;
        height: 100px;
        position: absolute;
      }
    </style>
  </head>
  
  <body>
    <div id="square" onclick='moveSquare()'></div>
    
    <script>
      let currentX = 0;
      function moveSquare () {
        currentX += 50;
        document.getElementById("square").style.left = currentX + "px";
      };  
    </script>
    
  </body>
</html>
```

Now, we are going to see how to do the same using the JavaScript method addEventListener().
The addEventListener() method attaches an event handler to the specified element. The addEventListener() method makes it easier to control how the event reacts to bubbling.

In the next example, we add an 'event listener' to the element 'square' with the code

```JS
document.getElementById("square").addEventListener("click", moveSquare);
```

This is the whole code

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title></title>
    <style>
      #square {
        background: green;
        width: 100px;
        height: 100px;
        position: absolute;
      }
    </style>
  </head>
  
  <body>
    <div id="square"></div>
    
    <script>
      let currentX = 0;
      function moveSquare () {
        currentX += 50;
        document.getElementById("square").style.left = currentX + "px";
      };  
      document.getElementById("square").addEventListener("click", moveSquare);
    </script>
    
  </body>
</html>
```
</br> 
</br>
## Exercises

You are going to use this code (let's call it 'Code A') to do the following exercises	
	
```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">

<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width" />
</head>
  
<body>

<p id="myTxt1">This is the paragraph number 1</p>
<p id="myTxt2">This is the paragraph number 2</p>
	
<button>Click me!</button>

</body>
  
</html>
```

**Exercise 1**. Modify 'Code A' so that the size of the text of paragraph 1 changes to "40px" if you click on paragraph 2.
	
**Exercise 2**. Repeat Exercise 1 using the JavaScript method addEventListener().
</br>
</br>
Now, you are going to use this code (let's call it 'Code B') to do the next three exercises

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">

  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title></title>
    <style>
      div {
        width: 100px;
        height: 100px;
        margin: 20px;
      }

      #square1 {
        background-color: red;
      }

      #square2 {
        background-color: blue;
      }
    </style>
  </head>
  
  <body>
    <div id="square1"></div>
    <div id="square2"></div>

    <script>
      let originalState = true;

      swapSquares = () => {
        originalState = !originalState;
        if (originalState) {
          // Add you JavaScript here
        } else {
          // Add you JavaScript here
        }
      };

      // Add the JavaScript listeners here
      
    </script>
  </body>
</html>
```

**Exercise 3**. Modify 'Code B' so that clicking on either square swaps their colours. (Use the JavaScript method addEventListener()).
Note that in this example, we are using an "arrow function". Don't panic! Both ways are equivalent.

```JS
swapSquares = () => {
...}

function swapSquares() {
...
}
```

## Adding a JavaScript Slideshow to a website

In this section, we are going to implement a JavaScript Slideshow to a website. In particular, we are going to add a Slideshow to the following webpage

<https://francescmarti00.github.io/dmu-multimedia/resources/ResponsiveSite/responsive/>

We can find the code of this webpage here <https://github.com/francescmarti00/dmu-multimedia/tree/master/resources/ResponsiveSite/responsive>
	
**Exercise 4**. This example allows us to display an array of images using JavaScript and - as always - the command getElementById. Every time we click on the image, we display the next image in the array. (Yes, again, there is a problem is we click on the image more than 3 times. We will fix this in the next exercise).





Add a function to 'Code C' so that the text of 'paragraph number 2' changes to green and text background changes to red if someone double-click on 'paragraph number 1'.

**Exercise 8 (Optional)**. Add a function to 'Code C' so that the text of 'paragraph number 1' changes to rgb(34, 56, 120) and text background changes to rgb(10, 255, 255) if someone click on the button.

Now, let's use this code (let's call it 'Code D') to do the following exercise.

```JS
<!DOCTYPE html>
<html>
  
<body>

<img id="myImage" src="https://www.w3schools.com/js/pic_bulboff.gif" style="width:100px">
	
<button>Click me!</button>

</body>
  
</html>
```

**Exercise 9**. Add a function to 'Code D' so that the bulb 'turn on' when you click on the button. (This is the JavaScript command to change the source of an image document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulbon.gif').		
</br> 

## JavaScript Conditional Logic
  
It is possible to have code execute based on a condition. If something is true, a thing will happen, otherwise it won't.
The condition logic can be used to store the 'status' of an element. Study this example

```JS
<!DOCTYPE html>
<html onclick='changeColor()'>
  
<body>

<p id="myTxt">Welcome to the easiest JavaScript example ever!</p>
   
<script>
  // Status is a variable
  // We are going to use status = 0 for black, and status = 1 for red
  let status = 0;
  function changeColor() {
    if (status == 0) {
      document.getElementById("myTxt").style.color="red";
      status = 1;
    } else {
      document.getElementById("myTxt").style.color="black";
      status = 0;
    }
}
</script>    

</body>
  
</html>
```
</br> 

## Exercises

Let's use the following code (let's call it 'Code E') to do the following two exercises.

```JS
<!DOCTYPE html>
<html onclick='changeColor()'>
  
<body>

<p id="myTxt">My text!</p>
   
<script>
  // Status
  let status = 0;
  function changeColor() {
    if (status == 0) {
      // Insert here the JavaScript command 1
      status = 1;
    } else {
      // Insert here the JavaScript command 2
      status = 0;
    }
}
</script>    

</body>
  
</html>
```

**Exercise 10**. Add two JavaScript commands to 'Code E' so that the text changes to bold if you click everywhere on the webpage. The text must change to normal if you click again.

**Exercise 11 (Optional)**. Add two JavaScript commands to 'Code E' so that the text background changes to red if you click everywhere on the webpage. The text background must change to white if you click again.

To do Exercise 12, we are going to use the following code (let's call it 'Code F').

```JS
<!DOCTYPE html>
<html>
  
<body>

<img id="myImage" src="https://www.w3schools.com/js/pic_bulboff.gif" style="width:100px">
	
<button onclick="changeImage()">On/Off</button>

<script>
  function changeImage() {
	document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulbon.gif'
  }
</script>    
  
</body>
  
</html>
``` 

**Exercise 12**. Modify 'Code F' so that the bulb 'turn on/off' when you click on the button.
</br> 

Finally, you are going to use the following code (let's call if 'Code G') to do the last exercises

```JS
<!DOCTYPE html>
<html onclick='countClicks()'>
  
<body>

<p id="myTxt">Let's count clicks!</p>
  
<script>
   // Let's define a variable. Its initial value is 0 (0 clicks)
   let x = 0;
   function countClicks() {
     // Every time we click on the button, we add '1' to the variable.
     x = x + 1;
     // Let's print the result!
     document.getElementById("myTxt").innerHTML = "You have clicked " + x + " times";
}
</script>  

</body>
  
</html>
```

**Exercise 13**. Create a program that changes the text background to red if, and only if you click on the webpage more than four times.

**Exercise 14 (optional)**. Create a program that changes the text background to blue if, and only if you click on a button between two and five times. So, if you click six time the text background must be white again.
</br> 

## Arrays

An array is a special variable, which can hold more than one value. For example:  

```JS
let animals = ["elephant", "gorilla", "leopard", "rhino", "turtle"];
```  

You access an array element by referring to the index number. So, animals[0] =  "elephant", animals[1] =  "gorilla", etc.

Study this example. Notice how we use the variable 'count' to display the array elements. (Yes, there is a problem is we click on the button more than 5 times. We will fix this in the next exercise).

```JS
<!DOCTYPE html>
<html>
<body>

<p id="theAnimal"></p>

<button type="button" onclick="countClicks()">Click me!</button>

<script>
  
  <!-- Let's define a variable. Its initial value is 0 (0 clicks) -->
  let count = 0;
  <!-- The array of animals -->
  let animals = ["elephant", "gorilla", "leopard", "rhino", "turtle"];
  
  function countClicks() {
    <!-- Let's print the brand name number 'count' -->
    document.getElementById("theAnimal").innerHTML = animals[count];
    <!-- Every time we click on the button, we add '1' to the variable 'count'. -->
    count = count + 1;
  }
  
</script>

</body>
</html>
```

**Exercise 15**. Modify your program in order to display the names of the animals in loop. That is, if you click on the button 6 times, your program has to show the first animal name "elephant", 7 times "gorilla", etc. (Tip: remember we can do this with the arithmetic operator Modulus. Remember that, for example 6 % 5 = 1, 7 % 5 = 2, etc.).

Finally, let's study this (very useful!) example. This example allows us to display an array of images using JavaScript and - as always - the command getElementById. Every time we click on the image, we display the next image in the array. (Yes, again, there is a problem is we click on the image more than 3 times. We will fix this in the next exercise).

```JS
<!DOCTYPE html>
<html>
  
<body>

<img id="myImage" src="https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/CardFlip/img/elephant.jpg" style="width:100px" onclick="changeImage()">
	
<script>
  var cont = 0;
  var imgArray = new Array();
  
  imgArray[0] = new Image();
  imgArray[0].src = 'https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/CardFlip/img/elephant.jpg';
 
  imgArray[1] = new Image();
  imgArray[1].src = 'https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/CardFlip/img/gorilla.jpg';
  
  imgArray[2] = new Image();
  imgArray[2].src = 'https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/CardFlip/img/leopard.jpg';
  
  function changeImage() {
    cont = cont + 1;
    document.getElementById('myImage').src=imgArray[cont].src
  }
</script>    
  
</body>
```

**Exercise 16**. Modify the previous example in order to display the animals in loop. That is, if you click on the image 3 times, your program has to show the pic of the elephant, 4 times the gorilla, etc.
