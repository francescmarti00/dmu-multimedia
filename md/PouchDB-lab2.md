## Working with Databases (2)

This task will have you creating a simple system to save data between sessions. To create and manage that data store we’re going to use PouchDB, an open source JavaScript database manager. PouchDB saves its data to local storage for persistence between sessions, and can optionally sync to a server-based database. This means that it saves its data in the browser. If you load the same site on a different computer, or even a different browser on the same computer, it will have its own instance of the database. This is quite limiting, but makes it simpler to explore the basics of using a database.

Using this we’re going to create a system to add the details and feedback of a user to the database using a form.

## Installing PouchDB

PouchDB is a fully JavaScript database manager, so installing it is just a case of including its single JavaScript file. You can either download this and host it locally, or link to the version on their CDN.

```JS
<script src="https://cdn.jsdelivr.net/npm/pouchdb@7.2.1/dist/pouchdb.min.js"></script>
```

You can find details of both options, and all about PouchDB on their website

<https://pouchdb.com>

## Creating an instance of PouchDB (an empty 'excel')

Once you’ve included the code, you need to create an instance of PouchDB to work with in JavaScript. So, either in a separate .js file or in a `<script>` element, create a new PouchDB instance and assign it to a variable. When you do this, you need to give PouchDB the name of the database. If the database already exists, it’ll just return that one to you.

```JS
let db = new PouchDB("usersData");
```

And... that is it! Our database is ready to use.

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title></title>
  </head>
  
  <body>

    <script src="https://cdn.jsdelivr.net/npm/pouchdb@7.2.1/dist/pouchdb.min.js"></script>
    
    <script>
      let db = new PouchDB("usersData");     
    </script>
    
  </body>
  
</html>
```

## Adding data to the Database

To add data to the database is straightforward. We just use the `put()` method that PouchDB provides, passing in the data.

xxx Let's suppose that we just want to save email addresses in our database. To do this we have to create an object. Let's call it `user`. This object includes two variables, the `_id` and the user email

```JS
let user = {
   _id: new Date().toISOString(),
   email: 'john@gmail.com'
}
```

In PouchDB each register, each 'email' in this case, is called a document. And each document is required to have a unique `_id`. Any subsequent writes to a document with the same `_id` will be considered updates. Here we are using a date string as an `_id`. For our use case, it will be unique, and it can also be used to sort items in the database. 

So, the data is ready, let's save it in the database with the `put()` method.

```JS
db.put(user);
```

So, the following code creates a PouchDB database (or instance) and save a document (an 'email' in this example) in it.

```JS
<!DOCTYPE html>
<html lang="en" dir="ltr">
  
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title></title>
  </head>
  
  <body>

    <script src="https://cdn.jsdelivr.net/npm/pouchdb@7.2.1/dist/pouchdb.min.js"></script>
    
    <script>
      let db = new PouchDB("usersData");
      
      let user = {
          _id: new Date().toISOString(),
          email: 'john@gmail.com'
      };
      
      db.put(user);    
    </script>
    
  </body>
  
</html>
```

Now, you can use the web inspector (Application tab) to check that this has worked and the email has in fact been saved.

![image](https://raw.githubusercontent.com/francescmarti00/dmu-multimedia/master/resources/Application.jpg)

Note that we can also use the web inspector to delete the database or their documents.

### Exercise 1:
Modify the variable `user` so the page also saves the name of the user and its 'rating score' for your website (a numberical value). So, the database saves the name, email and the rating score of an user.

## Creating a form

We have seen that add data to the database is straightforward. But it would be better to create a form to do this.

So, we need a form. We can create a form easily enough with HTML using the `<form>` element. We then populate the element with inputs. The kind of things you can put in a form include single line text input boxes, drop down selectors, multi-line text input, checkboxes and radio buttons. We just need the first one, single line text input boxes.

To create many of these types of input, we use the `<input>` element. We can then use its 'type' attribute to determine what kind of input it is. For a single line text box, we want the 'text' type. You can find a list of all the different types on the w3schools website -> <http://www.w3schools.com/html/html_form_input_types.asp>

```HTML
<input type="text" id="name" />
```

We also want to provide text labels for these boxes so the user knows what to enter in each one. We could just use `<p>` elements, but the `<label>` element provides a bit more context and meaning to robots and screen-readers.

We need to make sure each of those `<input>` elements has an `id` so that we can reference each with JavaScript in order to pull out the value.

We will also need a button on our form. We can achieve this with the `<button>` element. So, we have to add the folowing code to our webpage:

```html
<form>
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
    <input type="number" id="score" />
  </label>

  <button id="addUserFeedbackButton">Send your score!</button>
</form>
```

So, let's save the data of the form in the database. The first thing you’ll need to do is to be able to react to a click on that button, so add an event listener to it.

```JS
document.getElementById("addUserFeedbackButton").addEventListener("click", addUserFeedback);
```

The second thing, to create the addUserFeedback function, the function that gets run as a result of that event listener. This function will capture the form data and will save it in the database.

So, you have to end up with something like this:

```JS
    <script>
      let db = new PouchDB("usersData");
      
      function addUserFeedback() {
        let theDate = new Date().toISOString();
        let user = {
          _id: theDate,
          name: document.getElementById("name").value,
          email: document.getElementById("email").value,
          score: document.getElementById("score").value
        };
        
        db.put(user); 
      }
      
      document.getElementById("addUserFeedbackButton").addEventListener("click", addUserFeedback);
    </script>
```

And that’s it. You can use the web inspector to check that this has worked and the user feedback has in fact been saved.

### Exercise 2:
Modify the form input 'score' so users must select a numerical values (0-5) from a drop down selector.

## Getting Data Out: JavaScript HTML DOM Elements (Nodes)

Our UI will have two parts. One will be the form for adding the user feedback (we have already done this). The other will display a message saying "Thank you Mr. XXXX for your score XXX!".

The first thing we need to see is how to create new HTML elements using JavaScript. In the previous lab, we saw how to insert new rows in a table. Let's see now how to creaate new paragraph using javascript.

To add a new element to the HTML DOM, you must create the element (element node) first, and then append it to an existing element. (See <https://www.w3schools.com/js/js_htmldom_nodes.asp> for a detailed explanation).

```JS
<!DOCTYPE html>
<html>
<body>

<div id="div1">
  <p id="p1">This is a paragraph.</p>
</div>

<script>
  let para = document.createElement("p");
  let node = document.createTextNode("This text is in a new paragraph generated with javascript.");
  para.appendChild(node);

  let element = document.getElementById("div1");
  element.appendChild(para);
</script>

</body>
</html>
```

### Exercise 3 (Optional):
Modify the previous code so you create a new paragraph ("Paragprah 1",  "Paragprah 2", etc.) everytime you click anywhere in the page.

## Getting Data Out



## Getting Data Out

We also want to be able to retrieve data from our database. PouchDB provides us with the method `db.allDocs()` to get everything out of a database.

```Js
db.allDocs({ include_docs: true, descending: true }, showPizzas);
```

This method takes two parameters:

1. An options object.
2. A function to run when it's got results

But when do we want to run this? Well, ideally any time the contents of the database changes. To do this, we need to do two things:

1. Pop it in a function
2. Use PouchDB's `changes` method.

This first is easy.

```JS
functionloadPizzas () {
  db.allDocs({ include_docs: true, descending: true }, showPizzas);
};
```

For the second bit, just include the following JS underneath all your functions:

```JS
db.changes({
  since: "now",
  live: true,
}).on("change", loadPizzas);
```

Now it's time to write that `showPizzas()` function. This function will be given two things by PouchDB - details of any error, and the results if successful.

```JS
function showPizzas (err, doc) {
  console.log(doc.rows);
}
```

That `doc` object will have the results in if there wasn't an error. If you log the object the console and dig in, you'll see that the actual records are in a `rows` property, so it's `doc.rows` that we're interested in.

So, summarising, in order to display the database in the console, we have to add the following JavaScript code to our program

```JS
function showPizzas (err, doc) {
  console.log(doc.rows);
};

function loadPizzas() {
  db.allDocs({ include_docs: true, descending: true }, showPizzas);
};

db.changes({
  since: "now",
  live: true,
}).on("change", loadPizzas);

loadPizzas();
```

Finally, 

So, we want to loop over each entry in that `rows` array:

```JS
function showPizzas (err, doc) {
  doc.rows.forEach( row => {
    // we get each row here
  })
}
```

Within each row, the actual document is contained within a `doc` property.

```JS
function showPizzas (err, doc) {
  doc.rows.forEach( row => {
    let thisPizza = row.doc;
  })
}
```



## Going Further

This is simple example of saving and viewing documents. You could however go further in a number of ways. For example:

1. In the form, in the input fileds, create drop-down lists so you do not have to type the name of the pizza, price and toppings.
2. Add a button to remove all the list of pizzas (check `db.destroy()`).
3. Add a 'Checkout' button. This button should open a new page with the list of pizzas and total price.
4. Add an button what allows you to edit an existing pizza.
5. And of course, you could just make the whole thing look a lot better :)

For more info, visit: <https://pouchdb.com/getting-started.html>

## Conclusion

What we’ve seen here really only scratches the surface of databases, but it’s useful to get a handle on the issues to do with client-side and server-side data storage. There are pros and cons to each and being able to quickly spin up a database in either situation can be rather useful.
