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
### P1.2
### P1.3 
### P1.4
### P1.5 
### P1.6
### P1.7
### P1.8
### P1.9
### P1.10

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
- Intial the MongoDB**
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
