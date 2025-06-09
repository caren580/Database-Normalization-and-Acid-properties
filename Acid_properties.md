## ACID PROPERTIES
ACID is a set of properties that ensure reliable transactions in a database system. It stands for Atomicity, Consistency, Isolation, and Durability. These properties ensure that database transactions are processed reliably and help in maintaining the integrity of data across concurrent transactions.

## ATOMICITY
Atomicity guarantees that each transaction is treated as a single unit, which either succeeds completely or fails completely. There is no in-between state. If any part of a transaction fails, the database rolls back to its previous state, as if the transaction had never happened.

## CONSISTENCY
Consistency ensures that a transaction can only bring the database from one valid state to another. This maintains the data integrity by ensuring that any transaction will only be committed if it respects all database rules, including constraints, cascades, and triggers.

## ISOLATION
Consistency ensures that a transaction can only bring the database from one valid state to another. This maintains the data integrity by ensuring that any transaction will only be committed if it respects all database rules, including constraints, cascades, and triggers.

## DURABILITY
Durability ensures that once a transaction has been committed, it will remain so, even in the event of power loss, crashes, or errors. In PostgreSQL, this is managed through the use of write-ahead logging (WAL), which records changes before they are applied to the database.
![Properties image](ACID_PROPERTIES.webp)

## How ACID Properties Impact DBMS Design and Operation
1. Data Integrity and Consistency
ACID properties safeguard the data integrity of a DBMS by ensuring that transactions either complete successfully or leave no trace if interrupted. They prevent partial updates from corrupting the data and ensure that the database transitions only between valid states.
2. Recovery and Fault Tolerance
Durability ensures that even if a system crashes, the database can recover to a consistent state. Thanks to the Atomicity and Durability properties, if a transaction fails midway, the database remains in a consistent state.
3. Concurrency Control
ACID properties provide a solid framework for managing concurrent transactions. Isolation ensures that transactions do not interfere with each other, preventing data anomalies such as lost updates, temporary inconsistency, and uncommitted data.