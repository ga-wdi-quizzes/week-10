# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL DBs are table based databases that represent data in form of tables and require a predefined schema whereas NonSQL DBs are document based represented as collections of key-value pairs, documents, etc. with a dynamic schema of unstructured data.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
var result = AuthorModel.findOne({name: "Bob"});
console.log(result);
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: "Andy"}) {
  andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"});
}```

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
A module encapsulates related code into a single unit of code. When creating a module, we can interpret this as moving all related functions into a file.
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
app.get("/", function(req, res){
  response.send("show");
});
app.post("/", function(req, res){
  response.send("create");
});
app.put("/:id", function(req, res){
  response.send("update");
});
app.delete("/:id", function(req, res){
  response.send("delete");
});```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
The Rails framework is very organized and rigid in its rules and format the developer should follow. Express is much more forgiving and gives a lot of creative freedom to the developer.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js

```
