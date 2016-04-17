# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases use a relational model to manipulate data, making use of tables and columns.  NoSQL databases do not use a relational model.  Non-relational databases are very useful when the data being stored have little in common but it is necessary to retrieve them easily.  An example of this kind of dataset might be a large store inventory - many items exist, but they are likely to have few attributes in common (plush toy elephant vs bathroom tile cleaner).  Alternatively, relational databases are powerful and efficient when storing data that fit easily into a relational model; sports statistics, for example (teams, players, points, # of games, etc.).  
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
"AuthorModel.find" is not a viable method.  To return "results", the method should be written as "AuthorModel.findOne".
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
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

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

var bodyParser = require("body parser"); //neded for post requests

app.get("/", function(err, res){
  Model.find({}).then(function(models){
    console.log("Welcome");
    });
  });

app.get("/models/:name", function(err, res){
  Model.findOne({name: req.params.name}).then(function(model){
    console.log("Show");
    });
  });

app.post("/models/:name", function(err, res){
  Model.findOneAndUpdate({name: req.params.name}, req.body.model, {new: true}).then(function(model){
    console.log("Edit");
    });
  });

app.delete("/models/:name/delete", function(err, res){
  Model.findOneAndRemove({name: req.params.name}).then(function(){
    console.log("Delete");
    });
  });

```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is written in JavaScript, while Rails is written using the Ruby language.  Rails provides a lot of structure "out of the box" (file setup, etc.), while Express is a much cleaner framework.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js

```
