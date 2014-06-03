[![NPM](https://nodei.co/npm/mongomock.png?downloads=true)](https://nodei.co/npm/mongomock/)

mongomock
=========

mongoDb-native mocking library

Also the query engine works for basic js collections as well

Standalone version for a browser usage is [here](https://github.com/AndrewGrachov/mongo-query)

You can try a playground [here](http://andrewgrachov.github.io/mongo-query/)

#Dependencies
**bson**

#Install
```
npm install mongomock
```

#Getting started

```
var MongoMock = require('mongomock');

//initial mock data
var db = {
	fruits:[{name:'Banana',price:20},{name:'Apple',price:10,tags:['Africa','Turkey']},
	{name:'Orange',price:25},{name:'Pineapple',price:20}],
	beverages:[{name:'CocaCola',price:15},{name:'MongoCola',price:10},{name:'Pepsi',price:25}]
}

var mongo = new MongoMock(db);

mongo.collection('fruits').find({price:20},function(err,fruits){
  console.log("YAHOO we have fruits with price 20 now!",fruits);
})
```
**Update 0.0.3**
Now you are able to query your collections with string syntax, e.g., including arrays any level deep
```
db.fruits.find({'suppliers.name':'anonymous'});
//or
db.fruits.find({'suppliers.0.name':'anonymous'});
```

**Update 0.0.5**

Proper *findAndModify* support with upsert and 'new' options

**Update 0.0.8**

Proper string-based modifiers. '$' sign is not supported yet

``
db.fruits.update({}, {'suppliers.0.name' : 'anonymous'});
``

#Testing


Tests use mocha. Install mocha globally, then run

```
npm test
```

#Methods support
  **collection.find(query,options,callback)**

  **collection.findOne(query,callback)**

  **collection.update(query,modifier,options,callback)**

  **collection.insert(doc,callback)**

  **collection.remove(query,callback)**

  **collection.findAndModify(doc,modifier,options,callback)**

  **collection.save(doc,callback)**

#Query operators support:
  **$gte**

  **$gt**

  **$lt**

  **$lte**

  **$in**

  **$regex**

  **$and**

  **$or**

  **$ne**

  **$nin**

  **$size**

  **$elemMatch**

  **$exists**

  **$all**

#Modifier operators support
  **$set**

  **$unset**

  **$inc**

  **$addToSet**

  **$rename**

  **$pull**

  **$push**

  **$each**

#On the way
1. Date(and types) support
2. projections support

