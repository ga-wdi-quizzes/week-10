# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Although these are both databases with the purpose of storing and manipulating data, SQL and NoSQL databases have key differences in terms of both the terminology and functionality/capabilities.

Terminlolgy:
In NoSQL a ___ is a / __ in SQL
Collection / Table/View
Dynamic Schema / Fixed Schema
Embedded Documents / Joins

Some benefits to using a NoSQL database over a SQL is that NoSQL are more flexible and more room to scale. To illustrate this further, NoSQL has ability to scale horizontally and take in schemas (or other dynamic information not in a schema) that are not fixed. NoSQL is very good for storing volatile data.

For someone who is looking for a more fixed approach (e.g. link a bunch of documents together) and report statistics on this data, SQL is good at fetching arrays of data and storing it in both simple and complex environments.


```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// Mongoose requires a callback function
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
Instructor.findOne({name:"Andy"}, function(err, docs){
  docs.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"});
  docs.save();
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

```
@author = Author.create(name: "Andy" params[:name])

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```
Seperation of concerns is helpful because it allows for each piece or layer of code to be responsible for primarily one task. For compex apps, this reduces the responsibility of  the entire app into encapsulated units of functionality. Module.exports is important to this concept because it allows to reference / assign expressions in the modules  that are available for other files or routes.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/", function(req, res){
  console.log("Shows the app-welcome page")
  res.send("app-welcome");
});

app.post("/", function(req, res){
  res.send("Create");
});

app.put("/:id", function(req, res){
  res.send("Update");
});

app.delete("/:id", function(req, res){
  res.send("Destroy");
});
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```
Rails is a framework build on ruby that follows strict convention in terms of the syntax and organizational structure that builds the app. Rails starts with a good amount of code that people can build off of. Express on the other hand practically starts from scratch and it is up to the developer to build the routing system and links. Also, CRUD functionality is implemented differently in both. That is, Rails uses migrations whereas Express installs node modules.

```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```
Body parser requests bodies of code that support json objects. It extracts the entire body, which allows the app to see the entire contents of the body before parsing it. In terms of POST params, it allows express to grab information from the POST, create routes, and send information.

```
