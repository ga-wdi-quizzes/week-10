# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL uses tabeles and columns and is relational , NoSQL does not. you could use a NoSQl when storing data that does not have a relationship.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
  there would need to be a callback
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var Andy = Instructor.findOne({name: "Andy"})
Andy.save(function(err,instructor){
  if(err){
    console.log(err);
    }else{
      console.log(instructor)
    }
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
@andy.create(name: params[:name])

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
  takes all the code you need and allows it to be used in other files

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```

```js
app.get("/",function(res,req){
    res.send("read")
})

app.post("/",function(res,req){
  res.send("create")
})

app.put("/:something",function(res,req){
  res.send("update")
})

app.delete("/:anything",function(res,req){
  res.send("delete")
})
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
  Express does not generate boilerplate code
```

### Question #8

What is the importance of using body-parser in our express application for post requests? 

```js
  body parser is used to grab the data in a post request
```
