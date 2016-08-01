# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Your answer...
the structure is different.
SQL uses tables, rows, and columns - optimal for data that is relational because you can use foreign keys etc
no SQL is everything else - this type of DB doesn't often have as much structure (or schema). ex: mongoDB which uses collections and documents.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// Your answer...
mongo is asynchronous, so you need a callback function to console.log the results. so if you just
put the console.log(results) in a callback function then it should be ok
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
InstructorModel.findOne({name: "Andy"}, function(andy){
  andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"})
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
we can separate our files (like schema and seed files), and export modules so that we can use smaller bits of code like functions or models throughout the project.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/", function(req, res){
  response.send("Index")
})

app.post("/:id", function(req, res){
  response.send("create")
})

```

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
ruby is very structured and specific - it tells you how to do things and its better to follow their rules.
express gives you more freedom to structure your files as you want - there are less rules
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
we need body-parser to obtain user input from forms 
```
