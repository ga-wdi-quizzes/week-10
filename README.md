# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Sql databases are relational databases. NoSQL has more flexibility and does not require a relationship. If I was builing something between Teachers and Students I would most likely use SQL. But if I was doing soemthing more broad, such as A person who partakes in several different exercises that are unrelated to one another it may be easier to do NoSQL.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
There is no callback function inside.

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

@author = Author.create(name: String)

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```
Module.exports references the *current* module which emphasizes specification and singularity.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```
app.get("/", function(req, res){
  res.send("INDEX");
  });

app.post("/", function(req, res){
  res.send("CREATE");
  });


app.delete("/:id", function(req, res){
  res.send("DELETE");
  });


app.put("/:id", function(req, res){
  res.send("UPDATE");
  });

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails and Express differ in many ways.  Express is a very flexible framework, where as Rails will build a more specified framework for you.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
Body parser extracts a potion of the body from a request and is used with "req.body"
```
