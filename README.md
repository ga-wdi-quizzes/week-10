# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
As SQL DB is relational, with explicit one-to-one, one-to-many and many-to-many relationships. 
A NoSQL DB is non-relational, meaning it does not _necessarily_ have such relationshps. 

A NoSQL database works well with non-uniform data. It's alos faster with smaller data sets. 

Larger data sets will need SQL.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```text
find returns a list of documents, not a document. Even if there's only one bob, it will return a one item list 
containing bob the document, (If this was my family, it would return my brother-in-law Bob, my Uncle Bob on 
Mom's side, his son Bob, my Uncle Bob on Dad's side, and maybe his son Rob and the Bob I dated a little.)
```

```js
var results = AuthorModel.findOne({name: "Bob"});
console.log(results);
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

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
module.exports allows exporting code from one file to another. This allows files to focus on a given concern. 
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

What is the importance of using body-parser in our express application for post requests? 

```text
It's what allows us to parse the user inputs -- from a form, for instance.
```
