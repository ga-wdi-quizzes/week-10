# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Your answer...
All the data in SQL is relational built in a table. You can set unique properties and create a s

All the data in NoSql is non relation and can have data be inserted freely allowing it to be faster than a relation database
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```
There's no callback function

var results = AuthorModel.find({name: "Bob"}, function(results){
  console.log(results);
});


```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: "Andy"), function(err, andy){
  andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold");
  andy.save();
});
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
  @author = Author.create!(name: params[:name])
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
When separating code into individual modules we import that code into a single file

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
  res.render("index")
});
app.post("/", function(req, res){
  res
});
app.put("/:id", function(req, res){
  res
});
app.delete("/:id", function(req, res){
  res
});
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails uses Gems

express uses dependencies
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
 processes inputs received through a form and makes the post requests
```
