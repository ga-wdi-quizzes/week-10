#Week 10

##Mongoose

###Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

*SQL: Relational, structured, (tables, columns, rows, records), structure predefined and inflexible.
NoSQL: Non relational, non-structured (BSON key-value pairs, documents ), structure flexible and easy to change.*

*SQL is better for structured, defined, discrete items with exact specifications.   NoSQL is better for less structured environments that might need flexibility to change.*


###Question #2

What's wrong with this mongoose code and how might we fix it? (Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

*Mongoose has no "find" method; mongoose uses findOne, and the syntax is a little different.  The following should work:*

```js
var results = AuthorModel.findOne({'name': "Bob"});
console.log(results);
```


###Question #3

Convert the following ActiveRecord sequence to Mongoose:

```js
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```
*Here's my answer:*

```ruby
Instructor.update_all({:description => 'Resin Laying Deer Figurine, Gold'}, {:name => "Andy"})
```

###Question #4

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
*My answer follows:*

```ruby
def create
  @author = Author.new(author_params)

  respond_to do |format|
    if @author.save
      format.html { redirect_to @author, notice: 'Author was successfully created.' }
      format.json { render :show, status: :created, location: @author }
    else
      format.html { render :new }
      format.json { render json: @author.errors, status: :unprocessable_entity }
    end
  end
end
```

##Express

###Question #5

How does module.exports help us with separation of concerns?

*module.exports allows us to define an object in one file and execute it in another.  This allows us to maintain MVC separation of concerns; code can can be put in a controller and used by many models and views.*


###Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();
```
*My answer:*

```js
app.get('/', function (req, res) {
  res.send('GET');
});
app.post('/', function (req, res) {
  res.send('POST');
});
app.put('/', function (req, res) {
  res.send('put');
});
app.delete('/', function (req, res) {
  res.send('DELETE');
});

```

###Question #7

Describe the differences between Express and Rails as backend frameworks.

*Rails is very structured and opinionated; there's only one way to do things.  Express is much more flexible, although people tend to build MVC structures into it.*

*Rails has a bunch of commands that will build structures and folders and stub files for you.  Everything in Express has to be set up by hand.*

*Rails uses Ruby, Express uses JavaScript, which eliminates the need to train people in more than one language.*

*They both have extensive add-on libraries, Rails with GEM and Express with NPM.*


###Question #8

What is the importance of using body-parser in our express application for post requests?

*Body parser processes the body of the incoming request stream and provides functions for processing all types of data formats used for that purpose.  It then exposes that body to the program as **req.body**.  This could all be done with other Express/JavaScript tools, but body parser does it easily and simply.*  
