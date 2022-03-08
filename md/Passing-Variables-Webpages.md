# Passing variables from one webpage to another webpage

On some occasions, we need to pass variables from one webpage to other. For example, it is very common to pass the values of a form from a webpage to another.
There are several ways of doing this. Using URL parameters is probably the easiest way. In this lab we are going to see how to get a URL parameter with JavaScript.

## Submitting values through URL

Using URL parameters is probably the easiest way of passing variables from one webpage to another webpage. To submit values through URL is called GET method. There is also another method called POST. POST method needs PHP in order to get variables' values, so, we won't discuss this method in this lab.

The following image presents how variables are passed in webpage URL. Variables start after a question mark at the start, then the variable name – value pairs follow, separated by ampersands (&).

![image](https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/Passing_Var.png)

So, how to pass, how to submit the values of a form through URL? In fact, we don't have to do 'anything': the form submits these values by default.

Let's see the following example. This is the form:

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
Let's study the following example, the 'thanks.html':

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Thanks</title>
  </head>
  
  <body>
    
    <p>Thanks for the feedback <span id="thanks"></span>!</p>
    
    <script>
      // This is the URL of the page, which contains the form parameters
      let url = document.URL;
      
      // searchParams allows us to identily all the parameters in the URL
      let paramaters = (new URL(url)).searchParams;
      
      let name = paramaters.get("fname");
      
      // let's display the name!
      document.getElementById("thanks").innerHTML= name;
      
    </script>
  </body>
</html>
```

**Exercise 1**. Modify the previous example, so that the form includes the fields name, surname and email. All fields must be 'required'. The 'thanks.html' webpage must display the name, surname and email of the user.

**Exercise 2**. Add a radio button for users' gender with the fields 'Male', 'Female', and 'Other'. Display the users' gender in the 'thanks.html' webpage, along with the name, surname and email.

**Exercise 3 (Optional)**. Investigate how to add an 'Upload' button, so the user can upload his image using the form.

# Passing variables from one webpage to another webpage and saving them in a PouchDB database

As we have already seen, it is straightforward to save values of a form in a PouchDB database. For example, we can use a single webpage for the form, display a 'thanks' message and save the data into a database.  

The problem is that attributes  such as 'required' or 'pattern' may not work on this approach (we need to define a form 'action'). 

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Form</title>
  </head>
  
  <body>

    <form id="form1">

      <label for="fname">First name:</label><br>
      <input type="text" id="fname" name="fname"><br><br>

      <button id="addUserFeedbackButton">Register</button>

    </form>
    
    <p id="Submission Received"></p>

    <!---database--->
    <script src="https://cdn.jsdelivr.net/npm/pouchdb@7.2.1/dist/pouchdb.min.js"></script>

    <script>
      let db = new PouchDB("usersData");
      
      function addUserFeedback(event) {
        event.preventDefault();
        let theDate = new Date().toISOString();
                      
        // let's save in the database   
        let user = {
          _id: theDate,
          name: document.getElementById("fname").value
        };

        db.put(user);
        document.getElementById("form1").style.display = "none";
        thankYouText();
        }

        function thankYouText() {
          document.getElementById("Submission Received").innerHTML= "Submission Received";
        }
      document.getElementById("addUserFeedbackButton").addEventListener("click", addUserFeedback);
    </script>
  </body>
</html>
```

We can validate the form using Javascrip (see, for example, <https://www.w3schools.com/js/js_validation.asp>). However, the easiest way of validating and saving the form data into a database is by passing the variables to another webpage.

**Exercise 4**. Study the following example. In this example, the name of the user is submitted from the form to the webpage 'thanks.html'. In 'thanks.html' we save the name in the database.

The form:

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

      <button id="addUserFeedbackButton">Register</button>

    </form>
  </body>
</html>
```

The 'thanks' webpage

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
        name: paramaters.get("fname")
      };
      
      db.put(user);
      
    </script>
  </body>
</html>
```

**Exercise 5**. Modify your code so the 'thanks.html' webpage also displays the name of the user.<br>
**Exercise 6**. Add a radio button for users' gender with the fields 'Male', 'Female', and 'Other'. Save these fields in the database and display them in 'thanks.html'.
**Exercise 7 (Optional)**. Add the following fields in the form: Upload image, drop down selector for the user nationality, and email. You must save these fields in the database and display them in the 'thanks.html' webpage.
