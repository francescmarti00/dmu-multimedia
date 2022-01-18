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

In this section, we are going to implement a JavaScript Slideshow to a website. As we have already seen, to create a JavaScript Slideshow is straightforward.
This is the code we have seen in previous labs:

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">

<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width" />
</head>

<body>

<img id="myImage" src="https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/CardFlip/img/elephant.jpg" onclick="changeImage()">

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
    cont = (cont + 1) % imgArray.length;
    document.getElementById('myImage').src=imgArray[cont].src
  }
</script>    

</body>
```
</br>
</br>
## Exercises

In these exercises we are going to add a Slideshow to a webpage. In particular, we are going to add a Slideshow to the following webpage

<https://francescmarti00.github.io/dmu-multimedia/resources/ResponsiveSite/responsive/>

You can download the code here

<https://drive.google.com/file/d/1YWpQBOvnwmAZxngvEZMHJSn5aX3Yc0VE/view?usp=sharing>

You can download the new photos of the group here

<https://drive.google.com/file/d/1bdb8kvF79JuHDm025XnSWqopimRJ-q5k/view>


**Exercise 4**. Add a Slideshow the the previous webpage to display several photos of the group. So every time a user click on the group image, the webpage must display a new photo of the group. The images must be displayed 'in loop'.

In the webpage code, the photos of the group are displayed using this code

```JS
<img
  class="insetImage"
  src="img/CallaPhotoSmall.jpg"
  alt="Photo of the band"
/>
```

**Exercise 5 (Optional)**. In this exercise, you have to add a navigation button to the Slideshow you have just implemented.

In week 3, we created a similar Slideshow. You can see a completed example of the slideshow of week 3 here

<https://francescmarti00.github.io/dmu-multimedia/resources/SlideshowExample/>

Use this code as a reference for creating your navigation button:

<https://github.com/francescmarti00/dmu-multimedia/blob/master/resources/SlideshowExample/index.html>
