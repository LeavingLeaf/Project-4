# Project-4
- Created by Xiao Zhang and Aishwarya
## Contribution

|              Task              | Aishwarya | Xiao zhang |
| :----------------------------: | :-------: | :--------: |
|      1 Problem 1               |     3     |     3      |
|      2 Problem 2               |     3     |     1      |
| 3 Problem 3                    |     1     |     3      |


Where: 

- 3: Done Independently 
- 2: Done with help by partner
- 1: Giving Advice and Revise
- 0: Do nothing

## Problem 1

Install and execution Instructions:

 - Used Mongodb with Hadoop.

 - Started the Mongo shell with the command 'mongo' and 'mongod'.

 - Created a Database 'Peoplemongodb' and a collection 'famous-people' inside the database.

 - Inserted 10 documents to this collection from the link https://docs.mongodb.com/manual/reference/bios-example-collection/.

 - Performed CRUD Operations on the documents.


### P1.1
**Write an operation(s) that changes the _id of  “John McCarthy” to value  100.**

 myId=db['famous-people'].findOne({"_id" : ObjectId("51df07b094c6acd67e492f41")});

 db['famous-people'].remove({'_id':myId._id});

 myId._id=100;

 db['famous-people'].insert(myId);

 db['famous-people'].find({"_id" :100});
### P1.2
 **Write an operation(s) that inserts the following new records into the collection:**
 
 db['famous-people'].insertMany([
 {"_id":20,"name":{"first":"Mary","last":"Sally"},"birth":ISODate("1933-08-27T04:00:00Z"),"death":ISODate("1984-11- 07T04:00:00Z"),"contribs":["C++","Simula"],"awards":[{"award":"WPI Award","year":1999,"by":"WPI"}]},{"_id":30,"name":{"first":"Ming","last":"Zhang"},"birth":ISODate("1911-04-12T04:00:00Z"),"death":ISODate("2000-11-07T04:00:00Z"),"contribs":["C++","FP","Python",],"awards":[{"award":"WPI Award","year":1960,"by":"WPI"},{ "award":"Turing Award","year":1960,"by":"ACM"}]}])
{ "acknowledged" : true, "insertedIds" : [ 20, 30 ] }

 db['famous-people'].find({"_id":20});
 
 db['famous-people'].find({"_id":30});
### P1.3 

**Report all documents of people whogot a “Turing Award” after 1940.**
 
 myId=db['famous-people'].find({awards:{$elemMatch: {award:'Turing Award', year:{$gt:1940}}}});
### P1.4

 **Report all people who got more than 1award.**
 
 > myId=db['famous-people'].find({'awards.1':{$exists:true}});
 
 
### P1.5 
 **Update the document of “Guido van Rossum” to add “Python” to the contribution list.**
 myId=db['famous-people'].updateOne({'name.first':'Guido','name.last':'van Rossum'}, {$push: {contribs: 'Python'}});
 
 > db['famous-people'].find({"_id":6}); 

### P1.6
 **Insert a new fieldcalled “comments” of type array into document of “Mary Sally” storing the comments: “taught at2universities”, “was an amazing pioneer”, “lived in Worcester.”**
 
myId=db['famous-people'].updateOne({'name.first':'Mary', 'name.last':'Sally'},{$push: {comments: ['taught at 2 universities', 'was an amazing pioneer', 'lived in Worcester']}});
 
db['famous-people'].find({"_id":20});

### P1.7
**For each contribution by “Mary Sally”, say contribution “C”, list the people’s first and lastnames who have the same contribution “C”.  For example, since “Mary Sally” has two contributions in “C++” and “Simula”, the output for her should be similar to:{Contribution: “C++”, People:[{first: “Mary”, last: “Sally”}, {first: “Ming”, last: “Zhang”}]},{ Contribution: “Simula”,....}**

db['famous-people'].find({'name.first':"Mary",'name.last':"Sally"},{contribs:1}). forEach(function(x){ x.contribs.forEach(function(c) { myIds = db['famous-people'].find({'contribs':c}); print('{ Contribution: '+ "" + c + "", '}'); print('People : [');  myIds.forEach(function(myId) { print('{first:' +myId.name.first + ',last : ' + myId.name.last + '}'); }); print(']}'); }) });
### P1.8
**Report all documents where the first name matches the regular expression “Jo*”, where “*” means any number of characters.** 
db['famous-people'].find({'name.first':{$regex :'^Jo.*'}}).sort({'name.last':1});
### P1.9
**Update the award of document _id =30, which is given by WPI, and set the year to 1999.**

db['famous-people'].update({_id:30, 'awards.by':'WPI'},{$set:{'awards.$.year':'1999'}})

db['famous-people'].find({"_id":30});
### P1.10

**Add (copy) all the contributions of document _id = 3 to that of document _id = 30.**

myId=db['famous-people'].findOne({_id:3}, {contribs:1});

db['famous-people'].update({_id:30},{"$push":{"contribs":myId.contribs}})

db['famous-people'].find({"_id":30});

## Problem 2

Install and execution instructions: 

  - Used Mongodb with Hadoop.

  - Started the Mongo shell with the command 'mongo' and 'mongod'.

  - Created a Database 'Peoplemongodb' and a collection 'famous-people' inside the database.

 - Inserted 10 documents to this collection from the link https://docs.mongodb.com/manual/reference/bios-example-collection/.

 - Grouped documents in a collection and performed aggregation functions like count and sum.

 - Performed text search in MongoDB using a text index and $text operator.


### P2.1
### P2.2 
### P2.3 
### P2.4 
### P2.5
### P2.6

## Problem 3
Install and execution instructions:

**Environment**
 - MongoDB shell: v4.2.6
 - OS: Microsoft Windsow 10
 
**Construction Method**

 - Intial the MongoDB as a Local net Server
 - localhost: 127.0.0.1:27017
 - Username: -
 - password: -
 
**Execution** 

- Intial the MongoDB

**For P1 and P2**
- Run the DB_Initial_(1,2)_Parent-Referencing
- Then, Run the P1.1 or P1.2

**For P3, P4, and P5**
- Run the DB_Initial_(3,4,5)_Child-Referencing
- Then, Run the P1.3, P1.4, or P1.5
### P3.1
- query the "item" where “_id = MongoDB”;
- query the parent of the "item", save to "parents"
- Add the _id of parents to "ancestors"
- using a while loop to do the 2 process above, until the "Parents" is null, which means this is the top of the tree.
### P3.2
- Count the Up-level using the "Ancestors" method
- Count the Donw-level using the "Descendants" method
- Add them together minus the overlap, get the height of the tree.
### P3.3
- query the "item" where "children = dbm"
### P3.4
- query the "item" where "_id = Books"
- query the chilren of the "items"
- store item to current
- using the stack to recurse the following procedures:
 - store children to child
 - add child_id to decendant
 - stack.push child
### P3.5 
- quert the "item" where “_id == Databases”
- query the "parents" where "children = Databases"
- output the "siblings" from children of the "parents" when children != "item"
## References:
 - https://docs.mongodb.com/manual/reference/
 - https://stackoverflow.com/questions
