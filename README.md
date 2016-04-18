# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```
SQL is a relational database with a grid system that abstracts infor into a table
of rows and columns.  NoSQL databases are non relational and mixing and undoing
changes are more easily done. NoSQL databases are good for scaling and high performance.
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
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```
var andy = new Instructor({name: 'Andy'});
andy.wishlist_items.push({'description': 'Resin Layering Deer Figurine, Gold'});
vandy.save(function(err, res){
  err ? console.log(err) : console.log('andy was saved');
}

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

```

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```
It allows for code from one script file to be used in another.  So, you can
organize your code in separate files.
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

```
Express is minimal.  You get to put together an app piece by piece.  Rails give
you the entire app organization in a directory right away.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```
body-parser is middleware that parses data from html forms so you're app can use it.
```
