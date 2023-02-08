 - Modification statements are completed evaluated on the old state before producing a new state of the database
 - Basically and Select in the modification statement is before **ANY** modifications are made

## Serializability
 - Isolation layer that makes it appear that every transaction is done one by one
 - Even though there is a lot of transations happening at the same time

## Transactions

### Start transaction
 - Marks the beginnning of a transaction
 - Followed by one or more SQL statements

### Commit
 - Ends the transaction
 - All changes to the database caused by the SQL statements are commited
 - Permanent and visible
 - All changes become visible at ONCE (atomically)
 - Before commit, all changes are visible to this transaction, but NOT to other transaction

### Rollback
 - Causes the tranaction to abort
 - Any changes made by SQL statements within the transaction are undone
 - Reasons:
	 - Explicitly told to
	 - Deadlock
		 - Race Conditions

Dirty data is data that is written by a transaction but have not been commited yet
Dirty read refers to the read of dirty data written by another transaction
