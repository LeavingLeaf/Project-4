# MongoDB Statements
## Problem 1

Initialize 

> use Peoplemongodb

switched to db Peoplemongodb

> db

Peoplemongodb

> db.createCollection("famous-people")

{ "ok" : 1 }




Write an operation(s) that changes the _id of  “John McCarthy” to value  100.

> myId=db['famous-people'].findOne({"_id" : ObjectId("51df07b094c6acd67e492f41")});

> db['famous-people'].remove({'_id':myId._id});

> myId._id=100;

> db['famous-people'].insert(myId);

 db['famous-people'].find({"_id" :100});


## Problem 2
## Problem 3
### Environment
- MongoDB shell: v4.2.6
- OS: Microsoft Windsow 10
### Construction Method
- Intial the MongoDB as a Local net Server
  - localhost: 127.0.0.1:27017
  - Username: - 
  - password: -
