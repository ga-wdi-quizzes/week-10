# Week 10

### Question #3

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases are built around the idea of tables, rows (entries), and columns (attributes). SQL databases are optimized for relational data, and support relating data through JOIN operations and Foreign Keys. SQL databases have a rigid schema, which describes the structure of the tables and columns.

NoSQL databases often lack a schema, and allow us to insert any documents (similar to JSON objects) we want into the databases collections (related groups of objects). NoSQL can be faster for some cases, but slower when dealing with relational data.
```

### Question #4

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// This code is not using a callback function to process the results. Mongoose DB operations (find, save, etc) are all async, which means we need to pass a callback function to handle the results when they come back. Example below:

var results = AuthorModel.find({name: "Bob"}, function(results){
  console.log(results);
});
```

### Question #7

How is the concept of OAuth related to a valet key?

```text
You want to use their valet service so you give them your key (app ID and app secret) and in exchange they take your car and give you something to identify which car is yours (access token). (thx AlexS)

Also, valet keys allow you to give someone the keys to your car without full access (e.g. they can't open the trunk or glovebox). Similarly, OAuth allows you to share your account on a 3rd party provider (e.g. Facebook, Twitter, Google), without given the consumer app your password, or necessarily full access to your account, such as reading / modifying  your data, posting on your behalf, etc.
```

### Question 8

Write one Express route for each of four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```

```js
var express = require("express");
var app = express();

// Your code starts here...

app.get("/", function(request, response){
  response.send("SHOW");
});
app.post("/", function(request, response){
  response.send("CREATE");
});
app.put("/:id", function(request, response){
  response.send("UPDATE");
});
app.delete("/:id", function(request, response){
  response.send("DELETE");
});
// `app.patch` is also acceptable
// Not including `:id` is acceptable.
```

### Question 14

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: "Andy"), function(err, andy){
  andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold");
  andy.save();
});
```
