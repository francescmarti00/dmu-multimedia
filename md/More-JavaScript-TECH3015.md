# JavaScript Basics (part 2)

In this lab we will continue exploring JavaScript with examples and exercises.
</br> 
</br>  
## Welcome to the easiest JavaScript program ever!

### 1. HTML code

Study the following program. In this program there is no JavaScript, only HTML code. 

```JS
<!DOCTYPE html>
<html>
  
<body>

<p id="myTxt">Welcome to the easiest JavaScript example ever!</p>

</body>
  
</html>
```

### 2. The JavaScript getElementById() method

Let's create a very simple (and powerful) JavaScript command using the getElementById() method

![image](https://github.com/francescmarti00/dmu-multimedia/blob/master/resources/byId_1.png)

In this Figure, we can see how we can 'build' commands based on the getElementById() method

![image](https://github.com/francescmarti00/dmu-multimedia/blob/master/resources/byId_2.png)

For example, we can create the JavaScript command 

```JS
ondblclick='"document.getElementById("myTxt").style.fontSize="30px"
```

![image](https://github.com/francescmarti00/dmu-multimedia/blob/master/resources/byId_3.png)

Other examples could be

```JS
onclick='"document.getElementById("myTxt").style.color="red"
onmouseover='"document.getElementById("myTxt").style.fontWeight="bold"
```

### 3. Finally: how to connect these JavaScript commands and HTML

This is straightforward! We have just to put the JavaScript command inside the HTML tag we want to use as a 'control'. For example, we can put the JavaScript command inside the <html> tag, so if we click anywhere inside our web page, the JavaScript command will be run.

The next example shows how to change the font colour by clicking anywhere on the web page.

```JS
<!DOCTYPE html>
<html onclick='document.getElementById("myTxt").style.color="red"'>
  
<body>

<p id="myTxt">Welcome to the easiest JavaScript example ever!</p>

</body>
  
</html>
```

For example, we can use the attribute innerHTML to change the content of the element "myTxt"
	
```JS
<!DOCTYPE html>
<html onclick='document.getElementById("myTxt").innerHTML = "This is very easy!"'>
  
<body>

<p id="myText">Welcome to the easiest JavaScript example ever!</p>

</body>
  
</html>
```
	
### 4. So, do I need to memorise all the HTML Events and Attributes?
	
No.
	
No one remember all HTML Events and Attributes. For example, do you want to change the font of your text? Go to the w3shools css reference <https://www.w3schools.com/cssref/pr_font_font.asp>, look for the CSS font Property "font" and check what is the JavaScript syntax you have to use.

![image](https://github.com/francescmarti00/dmu-multimedia/blob/master/resources/byId_4.png)

Do you want to use other HTML events? Check <https://www.w3schools.com/TAGS/ref_eventattributes.asp>
</br> 
</br>	
## Exercises

You are going to use this code to do the following exercises	
	
```JS
<!DOCTYPE html>
<html>
  
<body>

<p id="myTxt">I am going to modify this text with JavaScript!</p>

</body>
  
</html>
```	
	
**Exercise 1**. Modify the original code so that the text changes to blue if you click anywhere on the web page.

**Exercise 2**. Modify the original code (attention, the original code, not the code you have created in Exercise 1) so that the text changes to bold if you double-click anywhere on the web page.

**Exercise 3**. Modify the original code so that the size of the text changes to "50px" if you move the mouse.
	
**Exercise 4**. Modify the original code so that the text changes to red if someone click on the text (attention, not on the web page, on the text).

**Exercise 5**. Modify the previous code so the text background changes to green if someone double-click on the text. You can check the JavaScript syntax in <https://www.w3schools.com/cssref/pr_background-color.asp>	
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

Use this code to do the following exercises

```JS
<!DOCTYPE html>
<html>
  
<body>

<p id="myText">Welcome to the easiest JavaScript example ever!</p>

</body>
  
</html>
```	
	
**Exercise 6**. Add a function to the original code so that the text changes to blue if you click anywhere on the web page.

**Exercise 7**. Add a function to the original code so that the text changes to bold and text background changes to green if someone double-click on the text (Attention, on the text, not on the web page).
</br> 

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

**Exercise 10**. Modify the previous code in order to display the name of the fourth brand "Renault".
**Exercise 11**. Create a program that displays the name of a car brand everytime you click on a button. So, if you click 1 time, the program should show the brand "Saab", if you click 2 times "Volvo", 3 times "BMW", etc.
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
