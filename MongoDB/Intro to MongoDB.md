**Insert a Document in MongoDB:**  

- db.collection.insertOne(data : dictionary, options : dictionary)
- db.collection.insertMany(data : list of dictionary, options : dictionary)

options :

{ordered : false} - > by default it is true

>> Create Collections

db.createCollection(<collection_name>, json)

in json the validations will be defined


## Motor

This is the official MongoDB driver for asynchronous Python apps.

>>>$ python -m pip install motor


INDEXING IN MONGODB

db.collection.createIndex() --> MongoDB only creates the index if an index of the same specification does not exist.

db.collection.getIndexes()

db.collection.createIndex( {Dictionary of Data} , {Dictionary of Options} )

Options :
"name" : "IndexName" -- Index names must be unique else error will come and you can't rename an existing index.

If you don't specify an index name, a default name is made which is the combination of key, _ and value for all pairs specified.
{"score" : 1 , "name" : 1} -- The index name is score_1_name_1


db.<collection>.dropIndex("<indexName>")
--> Drops the given index

db.<collection>.dropIndexes("<index1>", "<index2>", "<index3>")
--> Drops all index specified

db.<collection>.dropIndexes() 
--> Drops all index except _id

Types of Indexes :

1. Single Field Indexes : Single field indexes store information from a single field in a collection
db.<collection>.createIndex( { <field>: <sortOrder> } )

Indexing can be done on fields which have just values, fields that have embedded docs as the values and the embedded doc fields.

### Field Order for Embedded Documents

When you query based on embedded documents, the order that specify fields matters. The embedded documents in your query and returned document must match exactly.

db.students.createIndex( { "location.state": 1 } ) --> use the dot to specify

##
Compound indexes collect and sort data from two or more fields in each document in a collection. Data is grouped by the first field in the index and then by each subsequent field.

A single compound index can contain up to 32 fields.

