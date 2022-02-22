## Working with Forms

### HTML Forms
This task will have you creating a simple HTML form. An HTML form is used to collect user input. The user input is most often sent to a server for processing.

We can create a form easily enough with HTML using the `<form>` element. We then populate the element with inputs. The kind of things you can put in a form include single line text input boxes, drop down selectors, multi-line text input, checkboxes and radio buttons. We just need the first one, single line text input boxes.

To create many of these types of input, we use the `<input>` element. We can then use its 'type' attribute to determine what kind of input it is. For a single line text box, we want the 'text' type. This is an example of form with input fields for text:
 
```HTML
<form>
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" name="fname"><br>
  <label for="lname">Last name:</label><br>
  <input type="text" id="lname" name="lname">
</form>
```  

Note that we also want to provide text labels for these boxes so the user knows what to enter in each one. We could just use `<p>` elements, but the `<label>` element provides a bit more context and meaning to robots and screen-readers.

We need to make sure each of those `<input>` elements has an id so that we can reference each with JavaScript in order to pull out the value.  

But, how will a user submit this form? 

The `<input type="submit">` defines a button for submitting the form data to a form-handler. The form-handler is typically a file on the server with a script for processing input data. The form-handler is specified in the form's action attribute. If the `action` attribute is omitted, the action is set to the current page.
  
So, this is the code of a simple HTML form:

```HTML
<form action="/action_page.php">
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" name="fname" value="John"><br>
  <label for="lname">Last name:</label><br>
  <input type="text" id="lname" name="lname" value="Doe"><br><br>
  <input type="submit" value="Submit">
</form>
```

Notice that each input field must have a `name` attribute to be submitted. If the `name` attribute is omitted, the value of the input field will not be sent at all.
 
In this lab (and module) we won't discuss programming languages such as PHP or ASP, which allow us to create a file on the server with a script for processing input data. However, we can create an automatic message in our website by submitting the form to an HTML page (although, the data of the form won't be processed). (Optional: If you are very interested in knowing how to process form input data, please check <https://www.w3schools.com/php/php_forms.asp>. But this topic is not part of the module!).

```HTML 
 <form action="/thanks_message.html">
```  

### The HTML `<form>` Elements

The HTML `<form>` element can contain several form elements. Let's discuss the most important ones:
  
#### The `<input>` Element
  
The most used form element is the `<input>` element. There are different input types you can use in HTML, including 'text', 'number', 'date', 'email', etc. 

For example, `<input type="password">` defines a password field:

```HTML 
 <input type="password" id="pwd" name="pwd">
```  

For a detailed list of input elements, check <https://www.w3schools.com/html/html_form_input_types.asp>

#### The `<label>` Element

As we have already seen, the `<label>` element defines a label for several form elements. 

#### The `<select>` Element

The `<select>` element, in combination with the `<option>` element, defines a drop-down list:

```HTML 
<label for="cars">Choose a car:</label>
<select id="cars" name="cars">
  <option value="volvo">Volvo</option>
  <option value="saab">Saab</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
</select>
```  

To define a pre-selected option, add the `selected` attribute to the option:

```HTML 
  <option value="audi" selected>Audi</option>
```  

Use the `multiple` attribute to allow the user to select more than one value

```HTML 
<select id="cars" name="cars" size="4" multiple>
```  

#### The `<textarea>` Element

The `<textarea>` element defines a multi-line input field (a text area). The `rows` attribute specifies the visible number of lines in a text are, and the `cols` attribute specifies the visible width of a text area.

```HTML 
<textarea name="message" rows="10" cols="30">
Enter your message here!
</textarea>
```

### Exercise 1

In this exercise you are going to create a registration form for a website. The following image shows you the information this form must include (image from <https://www.tutorialstonight.com/html-code-for-registration-form-with-validation.php>):

![image](https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/registration-form.webp)

The form does not have to process the input data. However, a 'Submission received' message should be displayed after registration is completed (you could use `<form action="/thanks_message.html">`).

### Exercise 2 (Optional)

In the previous lab we saw how to save the data of a form into a PouchDB database.

Modify the code of Exercise 1 so your form display a 'Submission received' message, and save the data in a PouchDB database.

## Reminder: forms and PouchDB
Study the following code. This code allows us to save the data of a form into a PouchDB database.

Important things to check:
- Remember that if the `action` attribute is omitted, the action is set to the current page.
- Why did we include the `event.preventDefault()` method in this code?
- Note that in the form of this code the form is submitted by using a `<button>` elements, instead of a 'submit button' (`<input type="submit" value="Submit">`). Both approaches are correct.

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title></title>
  </head>
  
  <body>
        
    <form id="form1">
      <label for="name">
        Name
        <input type="text" id="name" />
      </label>
      <label for="email">
        Email
        <input type="text" id="email" />
      </label>
      <label for="score">
        Score
        <select type="number" id="score">
          <option value="0">0</option>
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
          <option value="4">4</option>
          <option value="5">5</option>
        </select>
      </label>
      
      <button id="addUserFeedbackButton">Send your score!</button>
    </form>
    
    <p id="thanksMessage"></p>

    <script src="https://cdn.jsdelivr.net/npm/pouchdb@7.2.1/dist/pouchdb.min.js"></script>
    
    <script>
      let db = new PouchDB("usersData");
      
      function addUserFeedback(event) {
        event.preventDefault();
        let theDate = new Date().toISOString();
        let user = {
          _id: theDate,
          name: document.getElementById("name").value,
          email: document.getElementById("email").value,
          score: document.getElementById("score").value
        };
        
        db.put(user);
        document.getElementById("form1").style.display = "none";        
        thankYouText();
      }
            
      function thankYouText() {
        document.getElementById("thanksMessage").innerHTML= "Thank you for your feedback";
      }
      
      document.getElementById("addUserFeedbackButton").addEventListener("click", addUserFeedback);
    </script>
    
  </body>
  
</html>
```
