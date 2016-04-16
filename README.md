# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases are relational while NoSQL databases aren't. SQL databases use tables while NoSQL databases use documents, key-value pairs and graphs (This means it doesn't have to adhere to a schema).

SQL databases are vertically scalable while NoSql is horizontal.

If you have a lot of data its better to use NoSQL, because the query time for SQL is really long

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
//Mongoose operations require callbacks since they're asynchronous

var results= AuthorModel.find({name: "Bob"}, function(results){
  console.log(results);
})
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: "Andy"}).then(function(instructor){
  instructor.whishlist_items.push({description:"Resin Laying Deer Figurine, Gold"});
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
@author = Author.create!(name: params[:name])

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text

A module takes a bunch related functions and saves it into a package of code that can be used in another file. This helps a lot with separations of concerns because you can create long functions in one file, export them with modules, and then require them in another file.
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
app.post("/:id", function(req, res){
  res.send("update");
});

app.delete("/:id", function(req, res){
  res.send('delete');
});


```


### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails used Active Record to give it CRUD functionality and PostgreSQL for creating relational databases. Express on the other hand uses Mongoose for CRUD functionality and MongoDB (non-relational database).
```

### Question #8

What is the importance of using body-parser in our express application for post requests? Then, please provide an example of an Express App POST request:

```js

// body-parser extracts the necessary data from incoming requests such as forms.
app.post("/person"), function(req, res){
  res.json(req.body);
});

```
