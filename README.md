# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
A Sql database relies on tables and it's inter relationship to one another. If you change one, you have to change all in matters such as deleting or altering. It relies on migrations to create the tables and to make changes to them. In a noSql database, everything can be changed within its own collection. When changes are made, it doesn't affect any others within the database and it doesn't require migrations to create or make changes to the database. It's as easy as going into the collection and making the edit. that's it!.

You would use a sql db if you are creating a database that has a more uniformed structure like blog posts. every post will have an image, content, timestamp, and a unique id.

In a nosql database, you can make your collection as unique as you want it. So for an HR department, they may want to use a nosql database because of the amount of change they will experience within their database with employees and each department may require different things.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
I believe it would have to be Author.find({name: "Bob"});
console.log(results);
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.find({name: "Andy"})
wishlist_items.create({name: "Andy", {description: "ResinLaying Deer Figurine, Gold"}})

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
  authors.create(function(req, res){
  var author =   
    })
}

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
It allows us to export specifically what we want other files to access. Like module.exports="mongoose" would allow other files like index.js to access anything within the mongoose db.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/something/:name", function(req, res){
  console.log(req.params.name);

app.post('something', function(req, res))

app.use(bodyParser.json());

app.listen(3001, function(){
  console.log("We are in business")
})
})
```

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```
Express uses a noSql db that can be easily used with Angular or other javascript languages without having to configure to other languages like ruby. Express uses Mongodb and Rails uses Active Record which is a Sql database. Both are great if you are sticking to a front end and back end that speaks the same language but can become complicated if not.

```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```

Body Parser allows express to read forms within html. Without a body parser, it doesn't read the form and ignore it. You cannot have a form without the body parser. 

```
