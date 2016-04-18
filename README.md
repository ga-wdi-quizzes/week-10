# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
1.SQL is relational database whereas NoSQL is non-relational database.
2. SQL dbs have predefined schema whereas NoSQL dbs have dynamic schema for unstructured data.
3. SQL dbs are vertically scalable whereas NoSQL dbs are horizontally scalable.
4. SQL dbs are good fit for complex queries whereas NoSQL dbs are not.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js


var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
The find method needs call beck function to know what to do with the result it finds.

var results = AuthorModel.find({name: "Bob"},function(result){
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
Instructor.findOne({name: "Andy"}, function(err, andy){
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

@author = Author.create!(name: params[:name])

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
 Instead of putting one chunk of code in one file to process it, module.exports let us to separate files into smaller portion. and call each files by forming "require" relations.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```
app.get("/", function(req, res){
  res.send("Read");
  });

app.post("/", function(req, res){
  res.send("Create");
  });

app.put ("/:id", function(req, res){
  res.send("Update");
  });

app.delete("/:id", function(req, res){
  res.send("Delete");
  });



```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is the framework that usually uses with Rudy(like Ruby on rails). Once it is install it come with huge built in package and structure. And it has a conventions to follow to make easy backend development. Express is javascript backend frameworks comes with much lighter built in package compare to rails.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
'Unlike rails, Express framework doesn't come with form function(post method). It requires 'body-parser' in order to process post request.'

```
