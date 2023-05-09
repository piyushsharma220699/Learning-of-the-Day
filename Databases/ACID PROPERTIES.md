
### What is a Transaction?

**A transaction is a sequence of operations that are executed as a single unit of work**, and a transaction may consist of one or many steps. A transaction access data using read and write operations.
If a transaction succeeds, the data that were modified during the transaction will be saved in the database. If some error occurs and needs to be cancelled or reverted, the changes that were made in the data will not be applied.

ACID is an acronym that stands for Atomicity, Consistency, Isolation, and Durability.

<H1>Atomicity</H1>
Atomicity ensures that a transaction is treated as a single, indivisible unit of work, either fully completed or fully rolled back. In other words, all the actions within a transaction must succeed or the transaction must be aborted, so that the database remains in a consistent state.

Eg: 

Let's say there are two bank accounts, Account A and Account B, and a user wants to transfer $500 from Account A to Account B. To do this, the transaction would typically involve two operations:

1.  Deduct $500 from Account A
2.  Add $500 to Account B

If atomicity is enforced, then both of these operations will be treated as a single, indivisible unit of work. This means that if either operation fails, the entire transaction will be rolled back, and both Account A and Account B will remain in their original states.

For example, if the transaction fails after deducting $500 from Account A but before adding $500 to Account B, then the entire transaction will be rolled back, and Account A will not be debited, and Account B will not be credited. This ensures that the database remains in a consistent state and that the funds are not lost or transferred partially.

Atomicity guarantees that transactions are either fully completed or fully rolled back, which helps to maintain data consistency and integrity in the database.

Eg:

START TRANSACTION
- Insert an instagram post for user with user_id=100
- Increase the total post count for user with user_id=100
END TRANSACTION 

(either both should happen or none)

---
**HOW DO WE CREATE A TRANSACTION?**

To create a transaction in a database, you need to follow a few basic steps:

1.  Begin the transaction: You can begin a transaction by using the BEGIN, START TRANSACTION, or BEGIN TRANSACTION statement. This indicates the start of the transaction and that all subsequent statements will be part of the transaction until it is either committed or rolled back.
    
2.  Execute the SQL statements: Once the transaction has begun, you can execute one or more SQL statements that make up the transaction, such as SELECT, INSERT, UPDATE, or DELETE. These statements should be carefully designed to ensure that they meet the requirements of the transaction.
    
3.  Commit the transaction: After executing the SQL statements, you can commit the transaction using the COMMIT statement. This indicates that the changes made by the transaction should be made permanent and visible to other users.
    
4.  Roll back the transaction: If any part of the transaction fails or encounters an error, you can roll back the transaction using the ROLLBACK statement. This indicates that all changes made by the transaction should be undone, and the database should return to its state before the transaction began.

![[Pasted image 20230430001951.png]]

<h1> Consistency </h1>
The database should move from one consistent state to another consistent state. Validation rules must be put in place to ensure data consistency. 

Take for example a database field called SSNUMBER(10). It can only accept a 10 digit numeric value (0 to 9), which must be enforced by a routine that rejects anything lower than 10 digits and cannot be greater than 10 digits.

### How do we ensure Consistency?

Through Triggers, Cascades and Constraints.
- Cascades : Cascades suggest that if you delete a particular role, you should delete everything associated with it. In SQL, "cascade" refers to the behavior of automatically propagating changes to related tables when a row is updated, deleted or inserted.

Eg: If there is a User table and a Post table. Now as all the posts are related to some user and the user is deactivated, then all the post rows related to that user_id should also get deleted from the posts table. Also, if there is another table which stores the total_posts_count value for a user_id, that row should also get deleted.
IF THE PARENTS GET DELETED, ALL THE CHILD ARE AUTOMATICALLY DIED OFF.

- Triggers : In SQL, a trigger is a special type of stored procedure that is automatically executed in response to certain events such as insert, update, or delete operations on a table.

![[Triggers-in-DBMS.png]]