# JavaScript Basics (part 5)

In this lab we will continue exploring JavaScript with examples and exercises.
</br> 

## Adding a JavaScript Navigation Menu to a website

The section 'How To' of the website w3schools (<https://www.w3schools.com/howto/>) includes very useful snippets for HTML, CSS and JavaScript.
In this section, we are going to run and analyse some of the navigation menus examples we can find in that website.

To begin with, we are going to see how to create a full screen overlay navigation menu.

**Exercise 1**. The following code creates a full screen overlay navigation menu. Run and analyse the following code.
In particular, add/remove the following elements from the code, to fully understand their function:
1) href="javascript:void(0)"
2) &times
3) &#9776

```JS
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {
  font-family: 'Lato', sans-serif;
}

.overlay {
  height: 100%;
  width: 0;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: rgb(0,0,0);
  background-color: rgba(0,0,0, 0.9);
  overflow-x: hidden;
  transition: 0.5s;
}

.overlay-content {
  position: relative;
  top: 25%;
  width: 100%;
  text-align: center;
  margin-top: 30px;
}

.overlay a {
  padding: 8px;
  text-decoration: none;
  font-size: 36px;
  color: #818181;
  display: block;
  transition: 0.3s;
}

.overlay a:hover, .overlay a:focus {
  color: #f1f1f1;
}

.overlay .closebtn {
  position: absolute;
  top: 20px;
  right: 45px;
  font-size: 60px;
}

@media screen and (max-height: 450px) {
  .overlay a {font-size: 20px}
  .overlay .closebtn {
  font-size: 40px;
  top: 15px;
  right: 35px;
  }
}
</style>
</head>
<body>

<div id="myNav" class="overlay">
  <a href="javascript:void(0)" class="closebtn" onclick="closeNav()">&times;</a>
  <div class="overlay-content">
    <a href="#">About</a>
    <a href="#">Services</a>
    <a href="#">Clients</a>
    <a href="#">Contact</a>
  </div>
</div>

<h2>Fullscreen Overlay Nav Example</h2>
<p>Click on the element below to open the fullscreen overlay navigation menu.</p>
<p>In this example, the navigation menu will slide in, from left to right:</p>
<span style="font-size:30px;cursor:pointer" onclick="openNav()">&#9776; open</span>

<script>
function openNav() {
  document.getElementById("myNav").style.width = "100%";
}

function closeNav() {
  document.getElementById("myNav").style.width = "0%";
}
</script>
     
</body>
</html>
```

**Exercise 2**. The following code creates a top navigation menu for smartphones / tablets with CSS and JavaScript. Run and analyse the following code.
In particular, note how the code simplifies by defining:

```JS
var x = document.getElementById("myLinks");
```

```JS
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<style>
body {
  font-family: Arial, Helvetica, sans-serif;
}

.mobile-container {
  max-width: 480px;
  margin: auto;
  background-color: #555;
  height: 500px;
  color: white;
  border-radius: 10px;
}

.topnav {
  overflow: hidden;
  background-color: #333;
  position: relative;
}

.topnav #myLinks {
  display: none;
}

.topnav a {
  color: white;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
  display: block;
}

.topnav a.icon {
  background: black;
  display: block;
  position: absolute;
  right: 0;
  top: 0;
}

.topnav a:hover {
  background-color: #ddd;
  color: black;
}

.active {
  background-color: #04AA6D;
  color: white;
}
</style>
</head>
<body>

<!-- Simulate a smartphone / tablet -->
<div class="mobile-container">

<!-- Top Navigation Menu -->
<div class="topnav">
  <a href="#home" class="active">Logo</a>
  <div id="myLinks">
    <a href="#news">News</a>
    <a href="#contact">Contact</a>
    <a href="#about">About</a>
  </div>
  <a href="javascript:void(0);" class="icon" onclick="myFunction()">
    <i class="fa fa-bars"></i>
  </a>
</div>

<div style="padding-left:16px">
  <h3>Vertical Mobile Navbar</h3>
  <p>This example demonstrates how a navigation menu on a mobile/smart phone could look like.</p>
  <p>Click on the hamburger menu (three bars) in the top right corner, to toggle the menu.</p>
</div>

<!-- End smartphone / tablet look -->
</div>

<script>
function myFunction() {
  var x = document.getElementById("myLinks");
  if (x.style.display === "block") {
    x.style.display = "none";
  } else {
    x.style.display = "block";
  }
}
</script>

</body>
</html>
```

**Exercise 3**. The following code creates a collapsed sidebar. The sidepanel opens when you click on the hamburger menu/bar icon. Run and analyse the following code.

```JS
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {
  font-family: "Lato", sans-serif;
}

.sidepanel  {
  width: 0;
  position: fixed;
  z-index: 1;
  height: 250px;
  top: 0;
  left: 0;
  background-color: #111;
  overflow-x: hidden;
  transition: 0.5s;
  padding-top: 60px;
}

.sidepanel a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
  transition: 0.3s;
}

.sidepanel a:hover {
  color: #f1f1f1;
}

.sidepanel .closebtn {
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 36px;
}

.openbtn {
  font-size: 20px;
  cursor: pointer;
  background-color: #111;
  color: white;
  padding: 10px 15px;
  border: none;
}

.openbtn:hover {
  background-color:#444;
}
</style>
</head>
<body>

<div id="mySidepanel" class="sidepanel">
  <a href="javascript:void(0)" class="closebtn" onclick="closeNav()">×</a>
  <a href="#">About</a>
  <a href="#">Services</a>
  <a href="#">Clients</a>
  <a href="#">Contact</a>
</div>

<button class="openbtn" onclick="openNav()">☰ Toggle Sidepanel</button>  
<h2>Collapsed Sidepanel</h2>
<p>Click on the hamburger menu/bar icon to open the sidepanel.</p>

<script>
function openNav() {
  document.getElementById("mySidepanel").style.width = "250px";
}

function closeNav() {
  document.getElementById("mySidepanel").style.width = "0";
}
</script>
   
</body>
</html> 
```

**Exercise 4**. In this example, when we click on the hamburger menu/bar icon, the sidebar opens and push this content to the right. Run and analyse the following code. 

```JS
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {
  font-family: "Lato", sans-serif;
}

.sidepanel  {
  width: 0;
  position: fixed;
  z-index: 1;
  height: 250px;
  top: 0;
  left: 0;
  background-color: #111;
  overflow-x: hidden;
  transition: 0.5s;
  padding-top: 60px;
}

.sidepanel a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
  transition: 0.3s;
}

.sidepanel a:hover {
  color: #f1f1f1;
}

.sidepanel .closebtn {
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 36px;
}

.openbtn {
  font-size: 20px;
  cursor: pointer;
  background-color: #111;
  color: white;
  padding: 10px 15px;
  border: none;
}

.openbtn:hover {
  background-color:#444;
}
</style>
</head>
<body>

<div id="mySidepanel" class="sidepanel">
  <a href="javascript:void(0)" class="closebtn" onclick="closeNav()">×</a>
  <a href="#">About</a>
  <a href="#">Services</a>
  <a href="#">Clients</a>
  <a href="#">Contact</a>
</div>

<button class="openbtn" onclick="openNav()">☰ Toggle Sidepanel</button>  
<h2>Collapsed Sidepanel</h2>
<p>Click on the hamburger menu/bar icon to open the sidepanel.</p>

<script>
function openNav() {
  document.getElementById("mySidepanel").style.width = "250px";
}

function closeNav() {
  document.getElementById("mySidepanel").style.width = "0";
}
</script>
   
</body>
</html> 
```

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


**Exercise 5**. Add a Slideshow the the previous webpage to display several photos of the group. So every time a user click on the group image, the webpage must display a new photo of the group. The images must be displayed 'in loop'.

In the webpage code, the photos of the group are displayed using this code

```JS
<img
  class="insetImage"
  src="img/CallaPhotoSmall.jpg"
  alt="Photo of the band"
/>
```

**Exercise 6**. In this exercise we are going to introduce the getElementsByClassName() method. In contrast with getElementsByID (that returns a single element), the getElementsByClassName() method returns a collection of elements with a specified class name(s). Run and analyse the following code. In particular, analyse how to access the collection of elements.

```JS
<!DOCTYPE html>
<html onclick="myFirstFunction()">

<head>

<style>
  .example {
    background-color: green;
  }
</style>

</head>  
  
<body>

<p class="example">This is the first paragraph.</p>
<p class="example">This is the second paragraph.</p>  
  
<script>
  function myFirstFunction() {
    var collection = document.getElementsByClassName("example");
    for (let i = 0; i < collection.length; i++) {
      collection[i].style.backgroundColor = "red";
    }
  }
</script>  

</body>

</html>
```

**Exercise 7 (Optional)**. Run and analyse the following slideshow from w3shools: <https://www.w3schools.com/howto/howto_js_slideshow.asp>. In particular, analyse the method getElementsByClassName(). 
</br> 

**Exercise 8 (Optional)**. As we have already mentioned, the section 'How To' of the w3schools (https://www.w3schools.com/howto/) includes very useful snippets for HTML, CSS and JavaScript. Navigate to the w3schools 'How To' section and study the examples implemented in the HowTo home.
</br> 

### Exercise 5 solution

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <link href="css/style.css" type="text/css" rel="stylesheet" />
    <link
      href="https://fonts.googleapis.com/css2?family=Amatic+SC&display=swap"
      rel="stylesheet"
    />
    <script
      src="https://kit.fontawesome.com/a89069ad2d.js"
      crossorigin="anonymous"
    ></script>
    <title></title>
  </head>
  <body>
    <header>
      <div class="contents">
        <img class="logo" src="img/smallLogo.png" alt="Logo" />
        <nav id="mainMenu">
          <i class="fas fa-bars" id="menuButton"></i>
          <div class="menuItem"><a href="index.html">Home</a></div>
          <div class="menuItem"><a href="tour.html">Tour</a></div>
          <div class="menuItem"><a href="records.html">Records</a></div>
          <div class="menuItem"><a href="contact.html">Contact</a></div>
        </nav>
      </div>
    </header>
    <article class="clearFloat">
      <section class="highlightSection col-right">
        <p class="centred">
          <span class="quote">"massive, pastorally apocalyptic music"</span> -
          NME
        </p>
      </section>
      <section class="col-left clearFloat">
        <p>
          Her Name Is Calla are an English post-rock band based in the English
          cities of Leicester and Leeds, England.
        </p>

        <img
          id="slideshow"
          class="insetImage"
          src="img/CallaPhotoSmall.jpg"
          alt="Photo of the band"
        />
        <p>
          After playing live throughout the United Kingdom to much critical
          acclaim, touring with iLiKETRAiNS and The Twilight Sad, Cult of luna,
          Maybeshewill and Sólstafir, they released their debut album, The
          Heritage, in 2008, which was also positively acclaimed, and was
          followed by a well-received headlining tour. The album lasts over 50
          minutes, despite only containing six tracks.
        </p>

        <p>
          In February 2009, they announced their arrival on the German label,
          Denovali Records. Denovali re-released The Heritage on vinyl in late
          2009.
        </p>

        <p>
          The band released The Quiet Lamb, containing 12 tracks and lasting
          over 75 minutes, on 8 November 2010. NME gave it a score of 8/10,
          describing it as "massive, pastorally apocalyptic music". The Sun
          called it a "ten-track jewel of a record" that engages the listener
          "in a rare and beautiful way". The Quiet Lamb is ranked the 12th best
          Post-rock album of all time in a poll of fans and reviewers with a
          critic's score of 83.
        </p>
      </section>
      <section class="newsletterSection highlightSection col-right">
        <h2>Newsletter</h2>
        <p>
          Sign up to our newsletter to keep up to date with what we're up to.
        </p>
        <form class="inlineForm">
          <input placeholder="Email Address" type="email" /><button>
            Sign Up
          </button>
        </form>
      </section>
      <section class="albumCovers">
        <a href="https://hernameiscalla.bandcamp.com/album/animal-choir"
          ><img src="img/albumCovers/animalChoir.jpg"
        /></a>
        <a
          href="https://hernameiscalla.bandcamp.com/album/a-wave-of-endorphins-ost-2"
          ><img src="img/albumCovers/endorphins.jpg"
        /></a>
        <a href="https://hernameiscalla.bandcamp.com/album/the-heritage"
          ><img src="img/albumCovers/heritage.jpg"
        /></a>
        <a href="https://hernameiscalla.bandcamp.com/album/navigator-2"
          ><img src="img/albumCovers/navigator.jpg"
        /></a>
        <a href="https://hernameiscalla.bandcamp.com/album/the-quiet-lamb"
          ><img src="img/albumCovers/quietlamb.jpg"
        /></a>
        <a href="https://hernameiscalla.bandcamp.com/album/swan"
          ><img src="img/albumCovers/swan.jpg"
        /></a>
      </section>
    </article>

    <footer>
      <div class="contents">
        <p>
          &copy; Her Name Is Calla 2020
        </p>
        <div class="socialFollow">
          <a href="https://twitter.com/hernameiscalla"
            ><i class="fab fa-twitter"></i
          ></a>
          <a href="https://www.facebook.com/hernameiscalla"
            ><i class="fab fa-facebook-f"></i></a
          ><a href="https://www.instagram.com/hernameiscalla/"
            ><i class="fab fa-instagram"></i
          ></a>
        </div>
      </div>
    </footer>

    <script src="js/calla.js"></script>
    <script>
      var cont = 0;
      var imgArray = new Array();

      imgArray[0] = new Image();
      imgArray[0].src = 'img/CallaPhotoSmall.jpg';

      imgArray[1] = new Image();
      imgArray[1].src = 'img/CallaPhotoSmall_filter1.jpg';

      imgArray[2] = new Image();
      imgArray[2].src = 'img/CallaPhotoSmall_filter2.jpg';

      imgArray[3] = new Image();
      imgArray[3].src = 'img/CallaPhotoSmall_filter3.jpg';
      
      function mySlideshow() {
        cont = (cont + 1) % imgArray.length;
        document.getElementById('slideshow').src=imgArray[cont].src;
      }
    
      document.getElementById("slideshow").addEventListener("click", mySlideshow);
    </script>
  </body>
</html>
```
