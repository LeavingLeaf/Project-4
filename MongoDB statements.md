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
 
 **Report all documents of people whogot a “Turing Award” after 1940.**
 
 myId=db['famous-people'].find({awards:{$elemMatch: {award:'Turing Award', year:{$gt:1940}}}});
 
 **Report all people who got more than 1award.**
 
 > myId=db['famous-people'].find({'awards.1':{$exists:true}});
 
 **Update the document of “Guido van Rossum” to add “Python” to the contribution list.**
 myId=db['famous-people'].updateOne({'name.first':'Guido','name.last':'van Rossum'}, {$push: {contribs: 'Python'}});
 
 > db['famous-people'].find({"_id":6}); 
 
 **Insert a new fieldcalled “comments” of type array into document of “Mary Sally” storing the comments: “taught at2universities”, “was an amazing pioneer”, “lived in Worcester.”**
 
myId=db['famous-people'].updateOne({'name.first':'Mary', 'name.last':'Sally'},{$push: {comments: ['taught at 2 universities', 'was an amazing pioneer', 'lived in Worcester']}});
 
db['famous-people'].find({"_id":20});

**For each contribution by “Mary Sally”, say contribution “C”, list the people’s first and lastnames who have the same contribution “C”.  For example, since “Mary Sally” has two contributions in “C++” and “Simula”, the output for her should be similar to:{Contribution: “C++”, People:[{first: “Mary”, last: “Sally”}, {first: “Ming”, last: “Zhang”}]},{ Contribution: “Simula”,....}**

db['famous-people'].find({'name.first':"Mary",'name.last':"Sally"},{contribs:1}). forEach(function(x){ x.contribs.forEach(function(c) { myIds = db['famous-people'].find({'contribs':c}); print('{ Contribution: '+ "" + c + "", '}'); print('People : [');  myIds.forEach(function(myId) { print('{first:' +myId.name.first + ',last : ' + myId.name.last + '}'); }); print(']}'); }) });

**Report all documents where the first name matches the regular expression “Jo*”, where “*” means any number of characters. Report the documents sorted by the last name.**

db['famous-people'].find({'name.first':{$regex :'^Jo.*'}}).sort({'name.last':1});

**Update the award of document _id =30, which is given by WPI, and set the year to 1999.**

db['famous-people'].update({_id:30, 'awards.by':'WPI'},{$set:{'awards.$.year':'1999'}})

db['famous-people'].find({"_id":30});

**Add (copy) all the contributions of document _id = 3 to that of document _id = 30.**

myId=db['famous-people'].findOne({_id:3}, {contribs:1});

db['famous-people'].update({_id:30},{"$push":{"contribs":myId.contribs}})

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
