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

For example, we can use the attribute inneHTML to change the content of the element "myTxt"
	
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

**Exercise 2**. Modify the original code so that the text changes to bold if you double-click anywhere on the web page.

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
</br>	
## Exercises

You are going to use this code to do the following exercises

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
