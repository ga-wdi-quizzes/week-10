# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
An SQL database requires data to be organized into a schema and each entry into a table defined by a schema will have all the attributes of that schema even if their value is null. Data entered into different tables can be linked to each other through join tables. Establishing relations between tables is the heart of SQL's awesomeness.

NoSQL databases have no required structure to records. Data can have many or few fields and those records can still be grouped together into a collection. If you have two collections you want to link together somehow you're going to have to do this through your program logic, not in the DB itself (NB: this fact is weird and jarring). The upside of NoSQL databases is that they are fast and a good choice if you have a bazillion variegated records.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js

var results = AuthorModel.find({name: "Bob"}, function(err, res){
  if (err){
    console.log(err);
  }
  else {
    console.log(res);
  }
});

```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

// I skipped this question and now that I'm back to it I'm skipping it for good because damn these quizzes take me a long-ass time.

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
@author = Authors.create!(name: params[:name])
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
module.exports allows us put related code into separate files and share that code between files as an object. Require the file and module.exports gives you the file's object.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Gimmie an R!
apt.get("/", function(req, res){
  res.send("index");
});
// Gimmie a C!
apt.post("/", function(req, res){
  res.send("create");
});
// Gimmie a U!
apt.put("/:id", function(req, res){
  res.send("update");
});
// Gimmie a D!
apt.delete("/:id", function(req, res){
  res.send("delete");
});
// What's that spell?!
// R-CUD!!(?)

```

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a Ruby-based framework that automatically creates an explicit file structure and comes with quite a bit of built-in data-handling conventions "inside the box". Express is a JavaScript-based framework that is much more flexible in terms of file structure and naming conventions but the flipside of that flexibility is that it requires more input and decision making on the part of the developer.

As an aside, I'm wondering how that structure vs flexibility tradeoff plays out when sharing code. I would think a dev coming to someone else's Rails app would have an easier time knowing where to find everything than if it was an Express app. True?
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
Body-parser is required for Express to process input when posting from forms.
```
