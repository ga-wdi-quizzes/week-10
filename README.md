# Week 10

## Mongoose

### Question #1

 Describe the differences between a SQL and NoSQL DB, and when you might use each.


SQL databases are primarily relational, table-based databases, whereas NoSQL databases are non-relational and primarily use key value pairs and groups. SQL databases have predefined schema for their relationships (as in rails), whereas NoSQL do not have separate pre-defined schema files.    
 ```

 ### Question #2
 What's wrong with this mongoose code and how might we fix it? (Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

 var results = AuthorModel.find({name: "Bob"});
 console.log(results);


// The code does not use the callback function required in the Mongoose DB. You could call it using function(results) as the second attribute to the find function.

 ### Question #3

Convert the following ActiveRecord sequence to Mongoose:

Instructor.findOne({name: "Andy"}, function(err, andy){
  andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold");
  andy.save();
};
});
 ```

 ### Question #4
Convert the following create method in Mongoose to ActiveRecord.
 }
 ```

-```rb
```@author = Author.create!(name: params[:name])

 ```
 ## Express
Convert the following create method in Mongoose to ActiveRecord.

 ### Question #5
 How does module.exports help us with separation of concerns?


module.exports is the thing (sometimes an object) that is returned as the result of a require call.


###Question #6
Write one Express route for each of the four HTTP methods.
 Then, make each route respond with a one-word string containing the RESTful action that would most likley be associated with this route.
 var express = require("express");
 var app = express();


1 app.get("/", function(req, res){
res.send("INDEX");
});

2  app.put("/:id", function(req, res){
  res.send("UPDATE");
});

3  app.post("/", function(req, res){
  res.send("CREATE");
});

4  app.delete("/:id", function(req, res){
  res.send("DELETE");
});..

 ```

var app = express();

 Describe the differences between Express and Rails as backend frameworks.

Express is a framework that leaves a lot of the specifics and decisions about the structure to the user/developer, whereas Rails is specific and much be structured a certain way in order for the framework to function.

 ```

 ### Question #8

-What is the importance of using body-parser in our express application for post requests?
What is the importance of using body-parser in our express application for post requests?

We use body-parser in express and node applications to take the data from users and make post requests.

 ```
