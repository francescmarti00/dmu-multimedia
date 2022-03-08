# Passing variables from one webpage to another webpage

In some occasions, we need to pass variables from one webpage to other. For example, it is very common to pass the values of a form from a webpage to another.
There are several ways of doing this. Using URL parameters is probably the easiest way. In this lab we are going to see how to get a URL parameter with JavaScript.

## Submitting values through URL

Using URL parameters is probably the easiest way of passing variables from one webpage to another webpage. To submit values through URL is called GET method. There is also another method called POST. POST method needs PHP in order to get variables' values, so, we won't discuss this method in this lab.

The following image presents how variables are passed in webpage URL. Variables start after a question mark at the start, then the variable name – value pairs follow, separated by ampersands (&).

![image](https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/Passing_Var.png)

So, how to pass, how to submit the values of a form through URL? In fact, we don't have to do 'anything', since, the form submit these values by default.

Let's see the folling example. This is the form:

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Form</title>
  </head>
  
  <body>

    <form id="form1" action="thanks.html">

      <label for="fname">First name:</label><br>
      <input type="text" id="fname" name="fname" required><br><br>
      
      <button id="addUserFeedbackButton">Register</button>

    </form>
  </body>
</html>
```

And this is the 'thanks.html' webpage.

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Thanks</title>
  </head>
  
  <body>
    
    <p>Thanks for your feedback!</p>

  </body>
</html>
```

## How to get URL parameters with JavaScript?

Probably, the easiest way of getting URL parameters with JavaScript is by using the method searchParams.
Let's study the following example:

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Thanks</title>
  </head>
  
  <body>
    
    <p id="thanks"></p>
    
    <script>
      // This is the URL of the page, which contains the form parameters
      let url = document.URL;
      
      // searchParams allows us to identily all the parameters in the URL
      let paramaters = (new URL(url)).searchParams;
      
      let name = paramaters.get("fname");
      
      // let's display the name!
      document.getElementById("thanks").innerHTML= "Thanks for the feedback " + name + "!";
      
    </script>
  </body>
</html>
```





```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Form</title>
  </head>
  
  <body>

    <form id="form1" action="thanks.html">

      <label for="fname">First name:</label><br>
      <input type="text" id="fname" name="fname" required><br>

      <label for="lname">Last name:</label><br>
      <input type="text" id="lname" name="lname" required><br><br>

      <!----gender---->
      <label for="gname">Gender</label><br>
      <input type="radio" id = "radMale" name="gender" value="male"> Male<br>
      <input type="radio" id = "radFemale" name="gender" value="female"> Female<br>
      <input type="radio" id = "radOther" name="gender" value="other"> Other<br><br>

      <button id="addUserFeedbackButton">Register</button>

    </form>
  </body>
</html>
```

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Thanks</title>
  </head>
  
  <body>
    
    <p>Thanks for your feedback! We have saved your data in our data base!</p>
    
    <!---database--->
    <script src="https://cdn.jsdelivr.net/npm/pouchdb@7.2.1/dist/pouchdb.min.js"></script>
    
    <script>
      let db = new PouchDB("usersData");
      
      // This is the URL of the page, which contains the form parameters
      let url = document.URL;
      
      // searchParams allows us to identily all the parameters in the URL
      let paramaters = (new URL(url)).searchParams;
      
      // let's save the info in the database
      let theDate = new Date().toISOString();      
      let user = {
        _id: theDate,
        name: paramaters.get("fname"),
        email: paramaters.get("lname"),
        gender: paramaters.get("gender")
      };
      
      db.put(user);
      
    </script>
  </body>
</html>
```
