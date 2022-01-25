# JavaScript Basics (part 5)

In this lab we will continue exploring JavaScript with examples and exercises.
</br> 

## Adding a JavaScript Slideshow to a website

In this section, we are going to add a JavaScript Slideshow to a website. As we have already seen, to create a JavaScript Slideshow is straightforward.
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

## Exercises

In these exercises we are going to add a Slideshow to a webpage. In particular, we are going to add a Slideshow to the following webpage

<https://francescmarti00.github.io/dmu-multimedia/resources/ResponsiveSite/responsive/>

You can download the code here

<https://drive.google.com/file/d/1YWpQBOvnwmAZxngvEZMHJSn5aX3Yc0VE/view?usp=sharing>

You can download the new photos of the group here

<https://drive.google.com/file/d/1bdb8kvF79JuHDm025XnSWqopimRJ-q5k/view>


**Exercise 1**. Add a Slideshow the the previous webpage to display several photos of the group. So every time a user click on the group image, the webpage must display a new photo of the group. The images must be displayed 'in loop'.

In the webpage code, the photos of the group are displayed using this code

```JS
<img
  class="insetImage"
  src="img/CallaPhotoSmall.jpg"
  alt="Photo of the band"
/>
```

**Exercise 2 (Optional)**. Run and analyse the following slideshow from w3shools: <https://www.w3schools.com/howto/howto_js_slideshow.asp>. In particular, analyse the method getElementsByClassName(). The getElementsByClassName() method returns a collection of elements with a specified class name(s).
</br> 

## Adding a JavaScript Navigation Menu to a website

The section How To <https://www.w3schools.com/howto/> of the website w3schools includes very useful snippets for HTML, CSS and JavaScript.
In this section, we are going to run and analyse some navigation menus.
