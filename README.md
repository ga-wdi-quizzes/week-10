# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL: SQL databases are relational and require a schema which helps normalize the data. They are more strict which can lead to greater data integrity. You'd want to use a SQL database for a project in which the data has more complicated relationships and data integrity is very important.

NoSQL: NoSQL databases are a lot more flexible and fast, and do not require a schema. They are not relational, so all of the data is in the same place. Because they're more flexible, they're easily scalable. You'd want to use a NoSQL database for a project in which data requirements are changing, and when scalability and speed are important.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```text
The code block is missing a callback function, or a promise so the console.log(results) could happen before the .find, because they're asynchronous, and it would error out. To prevent this, the console.log should be passed in a function after the .find so that it will always occur afterwards.
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

Instructor.findOne({name: "Andy"},function(response){
  response.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"});
  response.save();
})

```

### Question #4

Convert the following create method in Mongoose to ActiveRecord.

```js
  var authors = {
  create: function(req, res){
  var author = new AuthorModel({name: req.body.name})
  author.save(function(err){
    if (!err){
      res.redirect("authors")
    }
  })
  }  
}

```

```rb

@author = Author.create(name: params[:name])


```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
By separating code blocks into separate module files, you can require and access the code throughout an application. This makes it easier to organize code in a large application.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

get post put delete

app.get("/bands", function(req, res){
  res.send("index")
})

app.post("/bands", function(req, res){
  res.send("new")
})

app.put("/:name", function(req, res){
  res.send("update");
})

app.put("/:name", function(req,res){
  res.send("delete")
})

```

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a structured framework that has many rules or 'opinions' on how it should be used and how an application should be structured.

Express has far fewer opinions in how an application should be structured, leaving much more up to the user.


```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```text
Body-parser is necessary to process input forms from a user through express.


```
