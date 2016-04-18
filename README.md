# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text

SQL is a relational database, while NoSQL is not. This means NoSQL can be used for data that does not have the same properties (data in SQL have the same properties). SQL would be best used for a large amount of data and NoSQL for data that does not have the same properties.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js

Find would return an array of all the authors, in this case it would be an array of one.

To fix this:
var results = AuthorModel.findOne({name: "Bob"});
console.log(results);

```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

andy = InstructorModel.findOne({name: "Andy"});
wishlist_item1 = new Wishlist_itemModel({description: "Resin Laying Deer Figurine, Gold"});
andy.wishlist_items.push(wishlist_item1);

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
  @author = Author.create(author_params)
  redirect_to author_path(@author)
end

private
def author_params
  params.require(:author).permit(:name)
end

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```text

With module.exports, we can use different files for data, connections, and anything else related to the application being worked on. As long as we export and require files as necessary, this lets us separate our work to avoid one massive file of work.

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

//read
app.get("/authors", function(res, req){
  Author.find().then(function(authors){
    res.render("authors-index", {
      authors: authors
    });
  });
});

//create
app.get("/authors/:name", function(res, req){
  Author.findOne({name: req.params.name}).then(function(author){
    res.render("authors-show", {
      author: author
    });
  });
});

//update
app.put("/authors/:name", function(res, req){
  Author.findOneAndUpdate({name: req.params.name}, req.body.author, {new: true}).then(function(author){
    res.render("authors-show", {
      author: author
    });
  });
});

//delete
app.delete("/authors/:name", function(res, req){
  Author.findOneAndRemove({name: req.params.name}).then(function(){
    res.redirect("/authors")
  });
});
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text

Express is a lot faster since it requires more legwork (setting up connections, requiring dependencies, files, etc.); whereas, Rails is nicer, it does a lot of the work for you (ALL the files, automatic connections(as long as convention is followed), etc.)

```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```js

Body parser is used read the submitted contents of an HTML form.

```
