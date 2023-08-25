
All write operations in MongoDB are [atomic](https://www.mongodb.com/docs/manual/core/write-operations-atomicity/) on the level of a single document. When a single write operation (e.g. [`db.collection.updateMany()`] modifies multiple documents, the modification of each document is atomic, but the operation as a whole is not atomic.

Mongo Shell
[`db.collection.insertOne()`](https://www.mongodb.com/docs/manual/reference/method/db.collection.insertOne/#mongodb-method-db.collection.insertOne) inserts a _single_ [document](https://www.mongodb.com/docs/manual/core/document/#std-label-bson-document-format) into a collection.

Python
db.collection.insert_one(<dictionary>)
--> returns an instance of [`pymongo.results.InsertOneResult`]

db.collection.insert_many(<list of dictionary>)
--> 'insert_many' returns an instance of `pymongo.results.InsertManyResult`

If the collection does not currently exist, insert operations will create the collection.

In MongoDB, each document stored in a collection requires a unique [_id] field that acts as a primary key.

