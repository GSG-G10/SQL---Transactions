## Transactions in SQL Server 

<img src = 'https://data-flair.training/blogs/wp-content/uploads/sites/2/2018/08/What-are-the-transactions.jpg' width=1000px height=400px>

### What Is a Transaction? 
A transaction is a set of operations performed so all operations are guaranteed to succeed or fail as one unit.
Transaction is all or none
 
A common example of a transaction is the process of transferring money from a checking account to a savings account.
 
This involves two operations:

1- Deducting money from the checking account and
 
2- Adding it to the savings account.

Both must succeed together and the changes must be committed to the accounts, or both must fail together and rolled back so that the accounts are maintained in a consistent state. Under no circumstances should money be deducted from the checking account but not added to the savings account (or vice versa), you would at least not want this to happen with the transactions occurring with your bank accounts.
 
By using a transaction concept, both the operations, namely debit and credit, can be guaranteed to succeed or fail together. So both accounts remain in a consistent state all the time.

### When to use Transaction?
You should use transactions when several operations must succeed or fail as a unit.

When you use transactions, you put locks on data that is pending for permanent change to the database. No other operations can take place on locked data until the acquired lock is released. You could lock anything from a single row up to the entire database. This is called concurrency, which means how the database handles multiple updates at one time.
 
In the bank example above, locks will ensure that two separate transactions don't access the same accounts at the same time. If they do then either deposits or withdrawals could be lost.

>Note: it's important to keep transactions pending for the shortest period of time. A lock stops others from accessing the locked database resource. Too many locks, or locks on frequently accessed resources, can seriously degrade performance.
 

### Transaction State and Specifying Transaction Boundaries.
Transaction processing follows these steps:
1. Begin a transaction.
2. Process database commands.
3. Check for errors. 
   If errors occurred, 
       rollback the transaction, 
   else, 
       commit the transaction


### How to code transaction? and what if it fail's

The following three T-SQL statements control transactions in SQL Server:
1. BEGIN TRANSACTION: This marks the beginning of a transaction.
2. COMMIT TRANSACTION: This marks the successful end of a transaction. It signals the database to save the work.
3. ROLLBACK TRANSACTION: This denotes that a transaction hasn't been successful and signals the database to roll back to the state it was in prior to the transaction.

>Note: there is no END TRANSACTION statement. Transactions end on (explicit or implicit) commits and rollbacks.
