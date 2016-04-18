# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Your answer...
SQL databases are better when dealing with relational data and are more rigid in the designation of their schemas, they require items to have the same attributes and are laid out in rows and columns similar to a spreadsheet - NoSQL DBs allow for objects, called "documents" to be inserted into the database and these object can have different key value pairs.
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
missing  a callback function ---

var results = AuthorModel.find({name:"Bob"}, function(results){
  console.log(results)
})
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
Instructor.findOne({name: "Andy"},function(some callback?){
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
 @author = Author.create!(name: params[:name])
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
in modular programming code gets separated into modules that are interchangable and contain everything necessary to execute one aspect of functionality.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/", function(req, res){
  response.send("INDEX")
});

app.post("/", function(req, res){
  response.send("CREATE")
});

app.put("/:id", function(req, res){
  response.send("UPDATE")
});

app.delete("/:id", function(req, res){
  response.send("DELETE")
});

```

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
A LOT more freedom in Express - depending on what you are doing it can be faster - less bulk - dependencies can vary and really it seems that you can put code just about everywhere and it can still do it's job if constructed properly. Rails is very particular, one wrong move and you're out in the cold but it's still pretty great when you need that kind of structure to lean on.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```text
body-parser is used for translating the input in a form into usable data with which to make a post request. 

```
