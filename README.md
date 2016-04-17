# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Your answer...

SQL db:
- Relational database
- Uses foreign keys to join tables
- Rigid schema
- Queries(performance) can get expensive
- For use in complex relationship databases

NoSQL db:
- Non-relational database
- Document database
- High performance
- High availability
- Automatic scaling
- For use in databases with less complex associations or

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
//The find method requires a callback function to know what to do with the results it finds.
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
// Your answer...
Instructor.findOne({name: "Andy"}, function(err, andy){
  andy.wishlist_items.push({description: "Resing Laying Deer Figurine, Gold"});
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
In separation of concerns, we want to split the code up into portions each focused around one task/thing. module.exports helps us with this by encapsulating the portions that can then be called from other files.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/", function(req, res){
  res.send("Read");
});

app.post("/", function(req, res){
  res.send("Create");
});

app.put("/:id", function(req, res){
  res.send("Update");
});

app.delete("/:id", function(req, res){
  res.send("Delete");
});


```

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails provides much of the structure for your website. There are established conventions that must be followed for everything to work properly, such as using the correct path conventions.

Express provides the tools to build your own structure. For example, you choose your own path names. This makes the program much more lightweight, as most of the files are the ones you've created/defined.

```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```text
Because express is a lightweight framework, it doesn't know how to process user input received through a form and make a POST request with it. Including body-parser adds that functionality to express apps. You could argue that express should come with this library from the start, but it would be extra bloat for those who would never use it. 

```
