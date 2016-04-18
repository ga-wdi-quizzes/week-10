# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```
Sql database uses

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
var results = Author.findOne({name: "Bob"});
console.log(results);```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne(name: "Andy");
var Andy = mongoose.model('Andy', wishlist_items);
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
class Author < ActiveRecord::Base
  validates: name, presence: true

 def create
  @author = Author.create(name: params[:name])
  redirect_to_authors_path
 end

end
```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```It enables us to reference the item that's been exported anywhere by simply requiring the file that contains it.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/', function(req, res){
  res.send('hello world')
});

app.post('/' function(req, res){
  res.send('post req to page')
});

app.put('/instructor/:name' function(req, res){

    res.send('update');
});

app.delete('/instructor/:name)', function(req, res){
    res.send('destroy');
  
});
```

```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```Express is lightweight and fast while Rails is resourceful but slower.

Rails require migration to change Schema while express schema can be updated on the fly.


```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```
It enables us to get user input from HTML forms.

```
