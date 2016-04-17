# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text

SQL is a relational database while NoSQL is a database based on documents (non-relational).  In general, a NoSQL database lacks the structure of a relational database but offers more flexibility.  Therefore, they are ideal for less complex model associations.  In a SQL database, migrating data and schema can be annoying, but its rigidity is better suited for more complex models and relationships.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
var results = AuthorModel.findOne({name: "Bob"});
console.log(results);

```
.find method will result in an array.

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

app.get("instructors/:name", function(req, res) {
  Instructor.findOneAndUpdate({name: req.params.name, description: req.params.description}, req.body.object, function() {
    res.redirect("/instructors/" + Instructor.name);
  });
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
@author = Author.create(name: "Name")
redirect_to "index"

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text

module.exports allows elements of one .js file to be accessed in another .js file.  For example, one file could have "module.exports = mongoose.model("modelName")".  Another file can "require" mongoose and this modelname is available to use in the requiring file.  This allows for separate files to create a database and connecting it to mongoose.

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
app.get("/objects", function(req,res) {
  res.render("index-page");
})

app.get("/objects/:name", function(req, res) {
  Object.findOne({name: req.params.name}).then(function(object) {
    res.render("objects-show", {
      objects: objects
    });
  });
});

app.post("/objects", function(req, res) {
  Object.create(req.body.candidate).then(function(object) {
    res.redirect("objects/" + Object.name);
  });
});

app.post("/objects/:name", function(req, res) {
  Object.fineOneAndUpdate({name: req.params.name}, req.body.object, function() {
    res.redirect("/objects/" + Object.name)
  })
})

```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text

Two major diferences between Express and Rails are the database structure and back-end language.

In Express, javascript is used for both creating html views and the front-end.  In rails, Ruby controls the routes, views, and controllers.

A rails database has strictly-defined models and schema.  Express has more adaptability so it can interact with non-relational database.

```

### Question #8

What is the importance of using body-parser in our express application for post requests? Then, please provide an example of an Express App POST request:

```js

Body-parser is a middleware that allows NodeJS to process information received through forms.


app.use(parser.urlencoded({extended: true}));

app.post("/objects/:name", function(req, res) {
  Object.fineOneAndUpdate({name: req.params.name}, req.body.object, function() {
    res.redirect("/objects/" + Object.name)
  })
})

```
