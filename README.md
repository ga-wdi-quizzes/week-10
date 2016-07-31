# Week 10

## Mongoose

### Question #1

Describe the differences between an SQL and NoSQL DB, and when you might use each.

```text
SQL db's handle relational data better than NoSQL db's. SQL db's have strict schemas which have tables, columns and rows.

NoSQL db's don't require schemas, and can sometimes be faster than SQL db's.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```
```
It needs a callback.
```
```js
var results = AuthorModel.find({name: "Bob"}, function(results){;
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
Instructor.findOne({name: "Andy"}, function(andy){
  andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"});
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
@author = Author.create(name: params[:name])
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
It wraps code into an individual module, making it easier to "export" that specific code when needed.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", function(req, res){
  res.send("index");
});
app.post("/", function(req, res){
  res.send("create");
});
app.put("/:id", function(req, res){
  res.send("update");
});
app.delete("/:id", function(req, res){
  res.send("delete");
});

```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails seems to be more strict in how its structure is laid out.
Express isn't so picky in how you layout your apps structure.

```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```
It's needed to parse a users form input on a post request.
```
