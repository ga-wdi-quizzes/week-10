# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL is a relationship database, while noSQL has no relationships and therefore does not need to have rigid schemas.

NoSQL is easier to work with in the sense of less code and effort to update than SQL for smaller datasets. Large datasets need to be broken up or it's too much data that needs to be referenced at the same time.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
The console.log would return the full "result", in this case the hash. To return the author "Bob", use results.name
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...



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
  @author = AuthorModel.find(params)

end


```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text
Keeps seed data and building of model data in a separate file from the find and display of information.

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
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a convention over configuration/customization. Rails requires less code/time to set up... if you're okay with Rails opinions on how to set up models, transfer data, etc. Express doesn't have built-in opinions , which makes it a more customizable backend setup.

```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js
body-parser allows splitting of info JSON info.

```
