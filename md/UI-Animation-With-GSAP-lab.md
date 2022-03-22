# UI Animation With GSAP

This lab sheet sets you three challenges to accomplish using the GSAP animation tool from Greensock. In each case, you are provided with an example, so use that for reference if you get stuck.

In each case, you'll need to include the GSAP JavaScript file from Greensock. Visit their website to grab it, and access helpful documentation: <https://greensock.com/get-started>

## 1. Animated Menu

The first task is to create a simple animated menu.

Here's an example: <https://francescmarti00.github.io/dmu-multimedia/resources/animation/menu2.html>

You should use the GSAP method to() to animate it. 

You can use the following code as a starter:

````JS
<!DOCTYPE html>
<html>
  
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
  body {
    margin: 0;
  }
  
  .menuItem {
    padding: 5px;
    width: 100px;
    background-color: rgb(143, 207, 168);
    font-family: sans-serif;
    border-radius: 0 4px 4px 0;
    margin: 1px;
  }
</style>
</head>
  
<body>
  <nav>
    <div class="menuItem">Home</div>
    <div class="menuItem">About</div>  
    <div class="menuItem">Prints</div>
    <div class="menuItem">Contact</div>    
  </nav>  
</body>
  
</html>
````

## 2. Staggered Menu

Your task here is to create a menu where each menu item is animated onto the page in a staggered fashion - that is, one after the other.

Here's an example: <https://francescmarti00.github.io/dmu-multimedia/resources/animation/menu.html>

Without animation, the menu should sit in the top left of the page. You should use GSAP to animate it in **from** off the page. Use GSAP's stagger function to stagger each item's introduction.

## 3. Flipping Elephants

Your third task is to create an image that's introduced the page with a spin from the left.

Have a look at this: <https://francescmarti00.github.io/dmu-multimedia/resources/animation/photo.html>

There's a little styling on the image and its container, but mostly this is about using GSAP to animate several properties at once. As with the menu, have the image styled to be on the page by default, and then animate it **from** off the page. This means that if somebody is viewing your page without JavaScript, they'll still see the image.

## 4. Flipping Elephants (more complex!)

Based on the previous example, make a more complex animation using the parameters scale and opacity. 

## 5. Some examples (Optional)

Study and experiment with some examples you can find in <https://greensock.com/get-started>. You can get some ideas for your project from these examples!

## 6. Bouncing Ball (Optional)

Create a ball that falls and bounces to a stop in a fairly realistic way.

Here's an example: <https://francescmarti00.github.io/dmu-multimedia/resources/animation/ball.html>

There are two things to get right here. First is the use of border radius, radial gradient, and background position offset on a `<div>` to make it look like a ball. Use W3Schools for reference on the using a radial gradient for the background image (not the colour) and background position to offset it.

The second part is then using GSAP to give the ball a bounce.

