# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases are relational, while NoSQL databases are not. You might use NoSQL for user friendliness, while you might use SQL if each table needs to be large.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
Because you are using find instead of findOne, the results will be an array of objects.
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
I would use an Angular factory with this in Express:
Instructor.findOneAndUpdate({name: req.params.name}, req.body.instructor, {new: true})
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
@author = Author.new(author_params)
@author = Author.create!(author_params)
redirect_to author_url(@author)
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
It lets you control what data is shared between files.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// index
app.get("/api/doctors", function(req, res){
  Doctor.find({}).then(function(doctors){
    res.json(doctors)
  });
});

// show
app.get("/api/doctors/:name", function(req, res){
  Doctor.findOne({name: req.params.name}).then(function(doctor){
    res.json(doctor)
  });
});


// delete
app.delete("/api/doctors/:name", function(req, res){
  Doctor.findOneAndRemove({name: req.params.name}).then(function(){
    res.json({ success: true })
  });
});


// update
app.put("/api/doctors/:name", function(req, res){
  Doctor.findOneAndUpdate({name: req.params.name}, req.body.doctor, {new: true}).then(function(doctor){
    res.json(doctor)
  });
});

```

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is all about conventions; Express is more open-ended. Ruby vs JS.
```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
It lets you use information contained in HTML forms.
```
