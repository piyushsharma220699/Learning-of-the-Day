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

---
**HOW DO WE CREATE A TRANSACTION?**

To create a transaction in a database, you need to follow a few basic steps:

1.  Begin the transaction: You can begin a transaction by using the BEGIN, START TRANSACTION, or BEGIN TRANSACTION statement. This indicates the start of the transaction and that all subsequent statements will be part of the transaction until it is either committed or rolled back.
    
2.  Execute the SQL statements: Once the transaction has begun, you can execute one or more SQL statements that make up the transaction, such as SELECT, INSERT, UPDATE, or DELETE. These statements should be carefully designed to ensure that they meet the requirements of the transaction.
    
3.  Commit the transaction: After executing the SQL statements, you can commit the transaction using the COMMIT statement. This indicates that the changes made by the transaction should be made permanent and visible to other users.
    
4.  Roll back the transaction: If any part of the transaction fails or encounters an error, you can roll back the transaction using the ROLLBACK statement. This indicates that all changes made by the transaction should be undone, and the database should return to its state before the transaction began.

![[Pasted image 20230430001951.png]]

<h1> Consistency </h1>
