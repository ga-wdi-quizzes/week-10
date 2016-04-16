# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases are more structured and store information in tables with a predefined schema whereas a NoSQL databases can contain unstructured data (in documents) that may have multiple attributes that don't necessarily relate to one another. A SQL database should be used if the information being stored contains similar attributes, otherwise a NoSQL database should be used if the information has a range of unrelated attributes.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```text
The example provided needs to have a callback function so that the results of the query can be passed into the response.
```
```js
var results = AuthorModel.find({name: "Bob"}, function(err,data){
  console.log(data);
});

```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var Instructor = mongoose.model('Instructor', schema);

Instructor.findOne({"name": Andy}, function (err, andy) {
  console.log(andy);
  andy.wishlist_items.create({"description": "Resin Laying Deer Figurine, Gold")
}});
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
@author = Author.create(name: params[:name])
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
module.exports assists in adding all related functions into a single file that can accessed throughout the application.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();
```

```js
app.get("/", function(req,res){
  res.send("index")
});

app.post("/", function(req,res){
  res.send("create")
});

app.put("/:id", function(req,res){
  res.send("update")
});

app.delete("/:id", function(req,res){
  res.send("destroy")
});
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is written in Javascript so individuals who are familiar with Javascript may find it easier to work with. Express is also considered an unopinionated framework so there's no "right way".

Rails is a powerful framework that comes with a lot of out-of-the box functionality. The Rails community has "Convention over Configuration" mindset which embodies a "right way" of doing things to make the users life easier.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```text
Body-parser helps to process user-input received from a form.
```
