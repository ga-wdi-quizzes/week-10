# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL DB is Relational database with tables and predefined schemas whereas NoSQL is non Relational database which doesnt have table models and has key value pairs. PSQL is SQLDB and MongoDB is NoSQL.
I will use SQL when i know what data type is expected and will use NoSQL when im not sure of datatypes, i can get this DB started quickly.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
because its missing a callback function that can console log author model.
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
instructor.findOne.({name: "Andy"}),
dunction(err, andy){
  andy.wishlist_items.push({description: "Resin laying"});
  andy.save();
};

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
@author = Author.create!(name: params[:name])
```rb

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
Each module has all related codes in their own module and puts all codes in seperate file.
```

### Question #6

Write one Express route for each of the four HTTP methods.

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

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails uses ruby while express uses JS. Rails is more structured in creating the backend while express is not.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
body parses is used so that user input can be received and posted.
```
