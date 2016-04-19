# Week 10

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

> SQL databases are built around the idea of tables, rows (entries), and columns (attributes). SQL databases are optimized for relational data, and support relating data through JOIN operations and Foreign Keys. SQL databases have a rigid schema, which describes the structure of the tables and columns.

> NoSQL databases often lack a schema, and allow us to insert any documents (similar to JSON objects) we want into the databases collections (related groups of objects). NoSQL can be faster for some cases, but slower when dealing with relational data.


### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is `results` not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> This code is not using a callback function to process the results. Mongoose DB operations (find, save, etc) are all async, which means we need to pass a callback function to handle the results when they come back. Example below:

>```js
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

>```js
Instructor.findOne({name: "Andy"), function(err, andy){
  andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold");
  andy.save();
});
```

### Question #4

Convert the following create method in Mongoose to ActiveRecord.

```js
var authors = {
  create: function(req, res){
    var author = new AuthorModel(
    	{name: req.body.name}
    	);
    author.save(function(err){
      if (!err){
        res.redirect("authors");
      }
    })
  }  
}
```

>```ruby
@author = Author.create!(name: params[:name])
```

### Question #5

How does module.exports help us with separation of concerns?


>A module encapsulates related code into a single unit of code. By separating our code into individual modules, we are including all related functions into a single file.

### Question #6

Write one Express route for each of four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.


```js
var express = require("express");
var app = express();

// Your code starts here...

app.get("/", function(request, response){
  response.send("INDEX");
});
app.post("/", function(request, response){
  response.send("CREATE");
});
app.put("/:id", function(request, response){
  response.send("UPDATE");
});
app.delete("/:id", function(request, response){
  response.send("DELETE");
});

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.


> Rails is a very structured, opinionated framework written in Ruby, designed to support Relational Databases.

> Express, like Sinatra, is much less opinionated. We must explicitly state dependencies and configuration.  In return, we have a lot of freedom in how we structure our application (folders/files, how to load different files, managing dependancies, etc).

### Question #8

What is the importance of using body-parser in our express application for post requests? 


> In NodeJS and Express, we need to use body-parser middleware in order to process user input received through a form tag and make post requests.
