# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Your answer...
SQL (postgresql) is a relational database.
NoSql (Mongodb) is a non-relational database.
Both allow us to do CRUD functionality, but non-relational databases are best when you need flexibility or when you don't know how things will change and be added.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// Your answer...
Results would be a list of all documents that have the the name "Bob". AuthorModel is usually used when making a new model and creating a seed file.
In this case you would want to use the .findOne() function.
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
var andy = new InstructorModel({name:"Andy"});
var item1 = new WishlistModel({description: "Resin Laying Deer Figurine, Gold"})

andy.wishlists.push(item1)
andy.save(function(err, student){
  if(err){
    console.log(err)
  }
  else{
    console.log(student + " was saved to our db!");
  }
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
  @author = Author.create!(author_params)
  redirect_to "/authors/#{@author.id}"
end
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
It allows you to put things that are related in one file and then export it to another. All my schemas should be in one file and I can use them in another by exporting them and then requiring them in the file I want to use the schema in. When your project gets really long, this helps with organization.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Read
app.get("/candidates", function(req, res){
  //.find all candidates then
  //render to candidates index
  //use handle bars so it can be used in view
});
app.get("/candidates/:name", function(req, res){

});

//Create
app.post("/candidates", fucntion(req, res){
  Candidate.create(req.body.candidate).then(function(candidate){
    //redirect
  })
})

//Update
app.post("/candidates/:name", funciton(req, res){
  Candidate.findOneAndUpdate(
    //use body-parser and redirect.
  )
})

//Delete/Detroy
app.post("/candidates/:name/delete", function(req, res){
  Candidate.findOneAndRemove(
    //use body-parser and redirect
  )
})
```

```js
// Your answer...
GET
POST
PATCH
DELETE
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is an MVC framework written in Javascript. It runs on top of Node. Express uses Mongoose to talk with databases. Express works great with non-relational databases like Mongodb.

Rails is an MVC framework written in RUby. It runs on top of Webrick.  Rails uses ActiveRecord to talk with databases. Rails works better with relational databases like SQL or postgresql.

```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
Express does not have built in functionality for pulling information from forms. Express is lightweight so a lot of things are pulled from modules. In order to process user input received through a form we need to install and implement the body-parser middleware.
```
