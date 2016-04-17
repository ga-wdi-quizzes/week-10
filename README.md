# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL is a database that is called as Relational Database.
NoSQL is a database that is non-relational.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js

the code does not have a call back.
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.find({name:Andy,function(err, andy){
  andy.wishlist_items({description:"resin Laying Deer figurine, Gold"});
  andy.save();
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
@author = Author.create!(name:params[:name])
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
Module.exports by returning an object as a result of a require call which cause each function to do one thing at a time.
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
app.get(req, res){
  respond.send("index")});
app.put(req, res){
  respond.send("create")});
app.post(req, res){
  respond.send("update")});
app.delete(req, res){
  respond.send("delete")});
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express backend works with Javascript. Express is the backend part of the MEAN stack. There aren't any files that exist within the file.
Rails backend works with Ruby. Rails backend  have files made but aren't utilize until it created through the command line.

```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
Body-parser extracts the entire body portion of a request and exposes it on req.body.
```
