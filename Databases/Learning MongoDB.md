### Basics

- Document Oriented Database
- Open Source
- Written in C++
- Dynamic Database Schema
- The data is stored in BSON objects (Binary JavaScript Object Notation), which is similar to a JSON object but contains more datatypes than JSON. Eg: ObjectID, Date etc and also contains some additional information like 
	- **BSON File Extension :** .bson
	- BSON files are not human readable but can be extracted and parsed by programming languages or MongoDB Tools.
	- BSON is faster, requires more space & is used for storing the data.

### JSON vs BSON

![[JSONvsBSON.png]]

### Lazy Creation of resources in MongoDB

### Things to download On-Premise to run MongoDB

1. Basic MongoDB Community Edition : https://www.mongodb.com/try/download/community
2. MongoDB Compass : https://www.mongodb.com/products/compass
3. MongoDB Shell : https://www.mongodb.com/products/shell
4. MongoDB Drivers

![[Things2Download.jpg]]

### SQL vs MongoDB (Analogy)

![[SQLvsMongoDB.jpg]]

## Default Databases in MongoDB Cluster
---

There are three Default Databases : admin, config and local. In the admin database, a collection by the name system.version is present. In config database, system. sessions is present and in local database, startup_log collection is present.

![[DefaultCluster.jpg]]

Also, Here are the values present in the Collection :

#### system.version : 
![[System.Version.png]]

#### system.sessions :
![[System.Sessions.png]]

## DataTypes in MongoDB
---



## CRUD on Collections
---

#### CREATE (There are two ways) : 

One is using the createCollection function and other is directly adding a BSON Object in the Collection.
![[CreateCollectionsinMongoDB.png]]

$ db.createCollection(<collection_name/>)
OR
$ db.<collection_name/>.insertOne(<BSON Object/>)

#### READ

We can see what all collections are there in a MongoDB database
$ show collections

### UPDATE

### DELETE

$ db.<collection_name/>.drop()

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