# Passing variables from one webpage to other

In some occasions, we need to pass variables from one webpage to other. For example, it is very common to pass the values of a form from a webpage to another.
There are several ways of doing this. Using URL parameters is probably the easiest way. In this lab we are going to see how to get a URL parameter with JavaScript.

## Welcome to the easiest JavaScript program ever!



![image](https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/Passing_Var.png)

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
    <title>Form</title>
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
