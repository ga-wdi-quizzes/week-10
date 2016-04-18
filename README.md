# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text

NoSQL databases are non-relational, which means that the various collections in such a database do not need to be related to one another via foreign keys. In a SQL database, you must define a schema before you begin adding data (e.g., via ActiveRecord migrations in a Rails application), but a NoSQL database allows you to enter data right away, even if the structure of the data is not consistent. SQL databases are fairly rigid in structure, with tables, columns, and rows defined from the outset.

NoSQL databases provide high performance, high availability, and automatic scaling, but they do not perform as well when the data is relational. If there is a clear relationship between the different categories of content in a database (e.g., a post with many comments), SQL would be the better choice. On the other hand, a document-based, NoSQL database would work better if the data structure is less consistent, with individual documents not closely related to one another.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js

// The code above does not include a callback, and mongoose methods require a callback to work.

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

var andy = InstructorModel.findOne({name: "Andy"}, function(err, instructor){
  instructor.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"});
  instructor.save();
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

`module.exports` explicitly states what should be made available from a specific file, which allows us to control what information is read from one file to another. By using this method, we are able to separate related code (e.g., database schemata) into a single file.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

```

```js

app.get("/", function(req, res){
  res.send("index");
});

app.post("/", function(req, res){
  res.send("create");
});

app.put("/:name", function (req, res){
  res.send("update");
});

app.delete("/:name", function(req, res){
  res.send("destroy");
});

```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text

Rails favors convention over configuration, which means that there is usually one correct way to accomplish any particular goal (or a limited number of correct ways). Express, on the other hand, is very lightweight and only includes modules and packages that are explicitly stated by the developer. The consequence of this is that Rails give you a lot of different features out of the box, but Express allows you to decide exactly which features to include.

```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```text

Body parser allows us to read data submitted via HTML forms so that we can include full CRUD in an Express application. Essentially, any action that includes `req.body` will need the body parser middleware.

```
