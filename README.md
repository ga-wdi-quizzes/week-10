# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
A SQL DB like PostgreSQL gives a very concise data structure based on tables that carefully lays out a strict schema. A NoSQL DB like MongoDB allows a lot more flexibility with table schemas. You can pretty much get the initial set-up and implemented rather quickly.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```
```text
The example above had no callback function to perform any action with the results parameter.
```
```js
var results = AuthorModel.find({name: "Bob"}, function(results) {
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
def create
  @author = Author.create!(name: params[:name])
end
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
Module.exports allows us to have a completely separate file including code that we want to use in various different places and import it or "require" when needed in other files.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", function(req, res){
  res.send("INDEX");
});
app.post("/", function(req, res){
  res.send("CREATE");
});
app.put("/:id", function(req, res){
  res.send("UPDATE");
});
app.delete("/:id", function(req, res){
  res.send("DELETE");
});

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is like a more pure version of Rails, aside from the fact that Rails is written in ruby and not JavaScript. Rails comes with A LOT of out of the box helper methods and capabilities. That being said there is a lot of functionality Rails "does for you" that you don't know about and happens under the hood. Express is pure in the sense that it comes with almost nothing out of the box. You have to explicitly require every feature you want your app to have manually.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```text
In order to read data submitted via form from a user, we need a body-parser middleware to process the data.
```
