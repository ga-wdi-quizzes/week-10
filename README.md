# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL is a relational database that has a fixed schema for each table.  NoSQL stores data in objects that are collections, but each document doesn't have to have the same schema.

A good scenario for a NoSQL db would be when you have multiple models and their might be some ambiguity with the relationship(s) between them all, so a more flexible approach will be easier to work with.  Such as an HR database where you have managers and employees since some employees have multiple managers and managers have managers.

SQL databases are good well you have well defined relationships between models and there won't be much amongst the tables.  A post and comments app would be a good scenario to use a relational db.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js

var Author = mongoose.model("Author");

var bob = Authur.find({name: "Bob"});

console.log(bob)

```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

var andy = Instructor.find({name: "Andy"})



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

  module.exports only lets 

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
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text

```

### Question #8

What is the importance of using body-parser in our express application for post requests? Then, please provide an example of an Express App POST request:

```js

```
