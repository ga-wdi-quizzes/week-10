# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases are organized by tables, columns, and rows and are mainly used for relational data.  NoSQL databases allow you to insert any document you wish into the database, and can be a faster choice for non-relational data.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
It is missing a callback function to handle the results.

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
Modules group related code together so that all related functions are included in the same file.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", function(request, response){
  response.send("Index");
});
app.post("/", function(request, response){
  response.send("Create");
});
app.put("/:id", function(request, response){
  response.send("Update");
});
app.delete("/:id", function(request, response){
  response.send("Delete");
});

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is heavily structured and requires a you to write code in a more specific way.  Express gives you much more freedom when it comes to how you wish to structure your app.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
Body-parser must be used to process user input from forms in order to make a post request.
```
