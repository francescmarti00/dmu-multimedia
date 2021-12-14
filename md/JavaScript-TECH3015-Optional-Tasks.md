# JavaScript Basics (part 3)

In this lab we will continue exploring JavaScript with examples and exercises.
</br> 
</br>  
## Welcome back to JavaScript!

### 1. The JavaScript getElementById() method

As we have already seen, JavaScript is straightforward and easy to learn. With the JavaScript getElementById() method we can create very simple and powerful JavaScript commands. With these commands, we can change the font of a text, change its colour, background, size, to hide or change a paragraph or image, etc:

![image](https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/byId_1.png)

In this Figure, we can see how we can 'build' commands based on the getElementById() method

![image](https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/byId_2.png)

For example, we can create the JavaScript command 

```JS
ondblclick='"document.getElementById("myTxt").style.fontSize="30px"
```

![image](https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/byId_3.png)

Other examples could be

```JS
onclick='"document.getElementById("myTxt").style.color="red"
onmouseover='"document.getElementById("myTxt").style.fontWeight="bold"
```

### 2. How to connect these JavaScript commands and HTML?

This is also straightforward! We have just to put the JavaScript command inside the HTML tag we want to use as a 'control'. For example, we can put the JavaScript command inside the <html> tag, so if we click anywhere inside our web page, the JavaScript command will be run.

The next example shows how to change the font colour by clicking anywhere on the web page.

```JS
<!DOCTYPE html>
<html onclick='document.getElementById("myTxt").style.color="red"'>
  
<body>

<p id="myTxt">Welcome to the easiest JavaScript example ever!</p>

</body>
  
</html>
```

This example shows how to change the content of the element "myTxt" (using the attribute innerHTML) clicking on 'Welcome...'. (Note that the JavaScript command is inside the 'p' tag.). 
	
```JS
<!DOCTYPE html>
<html>
  
<body>

<p id="myText" onclick='document.getElementById("myTxt").innerHTML = "This is very easy!"'>Welcome to the easiest JavaScript example ever!</p>

</body>
  
</html>
```
	
### 3. So, do I need to memorise all the HTML Events and Attributes?
	
No.
	
No one remember all HTML Events and Attributes. For example, do you want to change the font of your text? Go to the w3shools css reference <https://www.w3schools.com/cssref/pr_font_font.asp>, look for the CSS font Property "font" and check what is the JavaScript syntax you have to use.

![image](https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/byId_4.png)

Do you want to use other HTML events? Check <https://www.w3schools.com/TAGS/ref_eventattributes.asp>
</br> 
</br>	
## Exercises

You are going to use this code (let's call it 'Code A') to do the following exercises	
	
```JS
<!DOCTYPE html>
<html>
  
<body>

<p id="myTxt">I am going to modify this text with JavaScript!</p>

</body>
  
</html>
```	
	
**Exercise 1**. Copy and paste the following JavaScript command onclick='"document.getElementById("myTxt").style.color="red" in 'Code A', so that the text changes to red if you click anywhere on the web page.
	
**Exercise 2**. Copy and paste the following JavaScript command onclick='"document.getElementById("myTxt").style.color="red" in 'Code A' ('Code A' is original program), so that the text changes to red if you click on the text.	

**Exercise 3**. Modify 'Code A' so that the size of the text changes to "40px" if you move the mouse.
	
**Exercise 4**. Modify the previous code so the text background changes to italic if someone double-click on the text. You can check the JavaScript syntax in <https://www.w3schools.com/cssref/pr_font_font.asp>

Now, you are going to use this code (let's call it 'Code B') to do the next two exercises	
	
```JS
<!DOCTYPE html>
<html>
  
<body>

<p id="myTxt1">This is the paragraph number 1</p>
<p id="myTxt2">This is the paragraph number 2</p>
	
<button>Click me!</button>

</body>
  
</html>
```		

**Exercise 5**. Modify 'Code B' so that the text of 'paragraph number 2' changes to blue if you click anywhere on the web page.

**Exercise 6**. Modify 'Code B' so that the text of 'paragraph number 1' changes to bold if you click on 'paragraph number 2'.
	
**Exercise 7**. Modify 'Code B' so that the text background of 'paragraph number 2' changes to blue if you click on the button. (You can check the JavaScript syntax in <https://www.w3schools.com/cssref/pr_background-color.asp>).
</br>
</br> 
## JavaScript Functions

### 1. A very simple example	
	
Ok, but how to change two or more attributes simultaneously? We can use a function!	
	
A JavaScript function is a block of code designed to perform a particular task. A JavaScript function is executed when "something" invokes it (calls it).
	
Study these two programs. They do the same!	

```JS
<!DOCTYPE html>
<html onclick='document.getElementById("myTxt").innerHTML = "This is very easy!"'>
  
<body>

<p id="myTxt">Welcome to the easiest JavaScript example ever!</p>

</body>
  
</html>
```
In this example, a JavaScript function is placed in the <body> section of an HTML page. The function is invoked (called) when we click on the web page.
	
```JS
<!DOCTYPE html>
<html onclick='myFirstFunction()'>
  
<body>

<p id="myTxt">Welcome to the easiest JavaScript example ever!</p>
  
<script>
  function myFirstFunction() {
  document.getElementById("myTxt").innerHTML = "This is very easy!";
}
</script>  

</body>
  
</html>
```	

### 2. Adding commands to a function	

One of the advantages of using functions is that we can run several JavaScripts events simultaneously.
Study this example. When we click on the web page we change two attributes: the text and colour of the text. 
	
```JS
<!DOCTYPE html>
<html onclick='myFirstFunction()'>
  
<body>

<p id="myTxt">Welcome to the easiest JavaScript example ever!</p>
  
<script>
  function myFirstFunction() {
	document.getElementById("myText").innerHTML = "This is very easy!";
	document.getElementById("myTxt").style.color="red";
}
</script>  

</body>
  
</html>
```	
</br>	

## Exercises

Use this code (let's call it 'Code C') to do the following exercises

```JS
<!DOCTYPE html>
<html>
  
<body>

<p id="myTxt1">This is the paragraph number 1</p>
<p id="myTxt2">This is the paragraph number 2</p>
	
<button>Click me!</button>

</body>
  
</html>
```	
	
**Exercise 8**. Add a function to 'Code C' so that the text of 'paragraph number 2' changes to green and text background changes to red if someone double-click on 'paragraph number 1'.

**Exercise 9**. Add a function to 'Code C' so that the text of 'paragraph number 1' changes to rgb(34, 56, 120) and text background changes to rgb(10, 255, 255) if someone click on the button.

Now, let's use this code (let's call it 'Code D') to do the following two exercises

```JS
<!DOCTYPE html>
<html>
  
<body>

<img id="myImage" src="https://www.w3schools.com/js/pic_bulboff.gif" style="width:100px">
	
<button>Click me!</button>

</body>
  
</html>
```		

**Exercise 10**. Add a function to 'Code D' so that the bulb 'turn on' when you click on the button. (This is the JavaScript command to change the source of an image document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulbon.gif').	
	
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

To do Exercise 11, we are going to use the following code (let's call it 'Code E').

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

**Exercise 11**. Modify 'Code E' so that the bulb 'turn on/off' when you click on the button.




## JavaScript Variables

To declare a variable in JavaScript we are going to use the the 'let' keyword.
  
```JS
let x = 0;
```

In this example, we are going to define a function called countClicks() that will count and display the number of times we click on the mouse.

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
</br> 

## Exercises

You are going to use this code to do the following exercises

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

**Exercise 8**. The module math operator %: In the original code, replace "x = x + 1" by " x = (x + 1) % 5 and study the result. Replace 5 by 8, and study the result.

**Exercise 9**. Modify the original code and use the event 'ondblclick' to invoke the function countClicks(). Change the function countClicks() in order to count the number of clicks correctly. That is, now the result should be 2, 4, 6 etc. 
</br> 
</br> 
## Arrays

An array is a special variable, which can hold more than one value. For example:  

```JS
let cars = ["Saab", "Volvo", "BMW", "Renault", "Mini"];
```  

You access an array element by referring to the index number. So, cars[0] =  "Saab", cars[1] =  "Volvo", etc.
  
In this code, let's define an array of car brands, and let's display the second brand "Volvo".
  
```JS
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Arrays</h2>

<p id="demo"></p>

<script>
let cars = ["Saab", "Volvo", "BMW", "Renault", "Mini"];
document.getElementById("demo").innerHTML = cars[1];
</script>

</body>
</html>
```  
</br> 

## Exercises

**Exercise 10**. Modify the previous code in order to display the name of the fourth brand "Renault".</br> 
**Exercise 11**. Create a program that displays the name of a car brand everytime you click on a button. So, if you click 1 time, the program should show the brand "Saab", if you click 2 times "Volvo", 3 times "BMW", etc.</br> 
**Exercise 12**. Modify your program in order to display the brands in loop. That is, if you click on the button 6 times, your program has to show the first brand "Saab", 7 times "Volvo", etc. (Tip: use the arithmetic operator modulus).
</br> 
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
  // status = 0 = black, status = 1 = red
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

**Exercise 13**. Create a program that displays a list of car brands if, and only if, you click on a button three times. Use the following code as a start.
  
```JS
<!DOCTYPE html>
<html>
<body>

<h2>Cars</h2>

<p id="demo"></p>

<script>
let cars = ["Saab", "Volvo", "BMW", "Renault", "Mini"];

function showCars() {
	// Your code here    
    }
</script>

<button type="button" onclick="showCars()">Click to display the list of cars!</button>

</body>
</html>
```  
  
**Exercise 14**. Create a program that displays a list of car brands if, and only if you click on a button more than two times.

**Exercise 15**. Create a program that displays a list of car brands if, and only if you click on a button between two and five times.  
</br> 
</br> 
## Loops
  
Loops in JavaScript enable us to perform the same code repeatedly.
</br> 

## Exercises

**Exercise 16**. Create a program that displays a list of car brands when you click on a button using a 'for' loop. Use the following code as a start.

```JS
<!DOCTYPE html>
<html>
<body>

<h2>Cars</h2>

<p id="demo"></p>

<script>
let cars = ["Saab", "Volvo", "BMW", "Renault", "Mini"];

function showCars() {
	// Your code here    
    }
</script>

<button type="button" onclick="showCars()">Click to display the list of cars!</button>

</body>
</html>
```  

**Exercise 17**. Repeat the previous exercise using a 'do/while' loop.  
