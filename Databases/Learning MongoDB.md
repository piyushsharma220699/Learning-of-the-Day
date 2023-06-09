
- Document Oriented Database
- Open Source
- Written in C++
- The data is stored in BSON objects (Binary JavaScript Object Notation), which is similar to a JSON object but contains more datatypes than JSON. Eg: ObjectID, Date etc and also contains some additional information like 
	- **BSON File Extension :** .bson
	- BSON files are not human readable but can be extracted and parsed by programming languages or MongoDB Tools.
	- BSON is faster, requires more space & is used for storing the data.

### JSON vs BSON

![[JSONvsBSON.png]]

### Lazy Creation of resources in MongoDB

## CRUD on Collections
---

#### CREATE (There are two ways) : 

One is using the createCollection function and other is directly adding a BSON Object in the Collection.
![[CreateCollectionsinMongoDB.png]]

$ db.createCollection(<collection_name/>)
OR
$ db.<collection_name/>.insertOne(<BSON Object/>)

#### READ

$ show collections


## CRUD on Documents
---

Below are the different CRUD operations you can perform on a document:

#### CREATE/INSERT DOCUMENTS IN THE COLLECTION (There are two ways):

insertOne() - Inserts a single document into the database

<db_name>.<collection_name>.insertOne(<BSON Object/>)

insertMany() - Inserts an array of BSON objects into the database.

<db_name>.<collection_name>.insertMany( [<BSON Object 1/> , <BSON Object 2/> ])

##### Here, we generally use db.<collection_name>.insertOne()/insertMany() because db == database being used.

![[Pasted image 20230609162102.png]]

Now, one receives MongoInvalidArgumentError if the argument is not a list, list is empty etc. Also, a syntax error if the BSON Object syntax isn't correct.

![[MongoErrors.png]]


### References

1. https://www.mongodb.com/developer/products/mongodb/cheat-sheet/
2. 