# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
An SQL is a database that is more restrictive in how the entries are organized. It requires that the schema of it's tables are well defined and restricted to singular values. A NoSQL database is not as restrictive but rather acts as a document reader the way that its data is organized. It can also accept arrays and nested objects as valid entries.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);

The code is not referencing a callback function to return the value. It requires this because mongoose DB is compiled asynchronously.

var results = AuthorModel.find({name: "Bob"}, function(results){
  console.log(results);

});
```

```js
// Your answer...
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")

Instructor.findOne({name: "Andy"}, function(err, result){
  result.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"});
  result.save();
  });
```

```js
// Your answer...
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
@author.create(name: params[:name])

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
Module.exports works similarly to a return statement in a function, in that it allows certain information to be passed freely from file to file like a function allows a value to be accessed outside itself. Using module.exports we are better able to divide up related parts of code into different files and then export and import the code as required.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```

```js
app.get("/", function, response{
  response.send("index")
});
app.get("/", function, response{
  response.send("create")
});
app.get("/", function, response{
  response.send("update")
});
app.get("/", function, response{
  response.send("delete")
});
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails relies heavily on convention over configuration, and as a result is looking for very specific pieces of code.
Express is a lightweight database framework that allows the user flexibility.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
Using the body-parser in our express application is important since it returns middleware that can process requests made through forms.
```
