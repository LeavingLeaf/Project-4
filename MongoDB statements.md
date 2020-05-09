# MongoDB Statements
## Problem 1

Initialize 

> use Peoplemongodb

switched to db Peoplemongodb

> db

Peoplemongodb

> db.createCollection("famous-people")

{ "ok" : 1 }




**Write an operation(s) that changes the _id of  “John McCarthy” to value  100.**

 myId=db['famous-people'].findOne({"_id" : ObjectId("51df07b094c6acd67e492f41")});

 db['famous-people'].remove({'_id':myId._id});

 myId._id=100;

 db['famous-people'].insert(myId);

 db['famous-people'].find({"_id" :100});
 
 **Write an operation(s) that inserts the following new records into the collection:**
 
 db['famous-people'].insertMany([
 {"_id":20,"name":{"first":"Mary","last":"Sally"},"birth":ISODate("1933-08-27T04:00:00Z"),"death":ISODate("1984-11- 07T04:00:00Z"),"contribs":["C++","Simula"],"awards":[{"award":"WPI Award","year":1999,"by":"WPI"}]},{"_id":30,"name":{"first":"Ming","last":"Zhang"},"birth":ISODate("1911-04-12T04:00:00Z"),"death":ISODate("2000-11-07T04:00:00Z"),"contribs":["C++","FP","Python",],"awards":[{"award":"WPI Award","year":1960,"by":"WPI"},{ "award":"Turing Award","year":1960,"by":"ACM"}]}])
{ "acknowledged" : true, "insertedIds" : [ 20, 30 ] }

 db['famous-people'].find({"_id":20});
 
 db['famous-people'].find({"_id":30});

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
