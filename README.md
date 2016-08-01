# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
No SQl - no need for uniform data - like firebase which is a type of noSQL database. No tables - yes documents and collections - documents are like a row in a table - and collections are whole data table. yes field pair values. no queries on foreign key ids usually faster except when dealing with relationship data, no JSON conversion size is limited

SQL - tables with firm structure of rows and columns best for relationship data and uses foreign keys

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);

no function - no results - no good for asynchronus operations

var results = AuthorModel.find({"Bob"}, function(res){
  console.log(res);

});
```

```js
// Your answer...
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
update: function(){
  Instructor.findOneAndUpdate({name: "Andy"}),
  {$push: {wishlist_items: {description: "Resin Laying Deer Figurine, Gold"}}, {new:true}
})
 this worked for my item push in Yum - I hope this is what you were looking for.
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
def create
 @author = Author.create!(name_params[:name])
```rb

```
## Express

### Question #5

How does module.exports help us with separation of concerns?

```Separation of concerns is the idea that each module or layer in an application should only be responsible for one thing.
creating a module is like moving all related functions into one file. (module.exports is the object that's actually returned as
the result of a require call) The module variable has a special property called the exports which is the value that is returned by a require call. So, it you set it to an object, the require call for this module will result in that object, if you set it to a function the require call returns that function.. In bottles of beer - module.exports let us separate our js files by exposing their contents as one
global variable which isn't assinged until we require the file.


```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```
// index
app.get("/", function(req, res){
    res.send("index");
});

//create
app.post("/", function(req, res){
  res.send("create");
});

//update
app.put("/:name", function(req, res){
  res.send("update");
});


//delete
app.post("/:name, function(req, res){
  res.send("delete");
});
```js
// Your answer...
```
### Question #7

Describe the differences between Express and Rails as backend frameworks.

```Express doesn't handle information posted from HTML forms you need to manually install middleware to get form data and
JSON data in a POST request - Rails already includes middlewar to hand this.

rails data base model: object-relational, dynamicSchema, NoSQL, xml database, schema-less, key-value, pub/sub, multidimensional
expres data base model: key-value, relational, redis, NoSQL

rails - Active-record, model view controlle, dependency injection - design pattern
express - model-view-controller

rails - ruby
express - node.js

rails database: microsoft bi, mongodb, mySQL, postgresSQL, Drizzle, Oracle, Redis, MYSQL, IBM DB@, CoucnDb, Cassandra
                MariadB, MemcacheDB, NoSQL, Microsof SQL Server Express, Edition
express database: MongoDB, mySQL

rails - web application framework for ruby
Express - web applicaion framework for node.js

rails target - web developement, app developement, media/publishing sector, system administration, employee/customer/vender
express target - web developement, app developement, Enterprise, Beginner

rails - structured - pretty rigid
express - free file structure, freely structured



```

### Question #8

What is the importance of using body-parser in our express application for post requests?

```Express doesn't handle information posted from HTML forms you need to manually install middleware, code that runs  
  inbetween receiving the request and responding,  to get form data and JSON data in a POST request - Rails already includes middlewar to hand this. so body-parser extracts the body of an incoming request stream and exposes it on as something easier to interface with. - body parser will parse the raw content.

```
