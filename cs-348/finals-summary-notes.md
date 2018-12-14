# Finals Summary Notes
## Optimization

- **Clustering index** - tuples in the relation with similar values for A are stored together in the same block
- **Non-clustering** - Other indices that are not clustering indices (also called secondary indices)

- Equivalences
- Operator implementation

- Not computationally possible to find an optimal plan

##### Simple Cost Model for disk I/O

**Uniformity**: All possible values of an attribute are equally likely to appear in a relation

**Independence** - the likelihood that an attribute has a particular value does not depend on values of other attributes

### Join Order

- Try to order intermediate results
- Nested loop join's cost is not symmetric

### Pipelined Plans

- All operators (except sorting) operator without storing intermediate results
    - No recomputation for left-deep plans
    
### Temporary Store

- General pipelined plans lead to recomputation

- Introduce store operator
    - Store intermediate result in a relation
    - Build a hash index

### Hardware Parallelism

- Multiple mass storage units
- Relational operators amenable to parallel execution

## Concurrency

### ACID Requirements

**Atomicity** - all or nothing execution

**Consistency** - execution preserves database integrity

**Isolation** - transaction execute independently

**Durability** - update made by a committed transaction will not be lost of subsequent failure

#### Implementation of Transaction Depends on

- **Concurrency control** - transactions do not interfere

- **Recovery Management** - committed transactions are durable, aborted transactions have no effect on the database

### Serializable Schedules

- An execution is serializable if it is equivalent to a serial execution of the same transactions

### Conflict Equivalence

- Two operations conflict if they
    - Belong to different transactions
    - Access the same data item
    - At least one of them is a write operation
    
### Recoverable Schedules

1. $$T_j$$ reads a value $$T_i$$ has written
2. $$T_j$$ succeeds to commit
3.  $$T_i$$ tries to abort


- In this situation we need to undo the effects of $$T_j$$ before we can abort $$T_i$$

- To avoid this, we should commit only in order of the read-from dependency

### Cascadeless Schedules

- Referring to the previous example, by aborting one transaction, it may lead to cascading aborts of many other transactions

- No reading of uncommitted data

### Get Serializable Schedule

- Operations that a scheduler can perform
    - Execute
    - Delay
    - Reject
    - Ignore
    
    
- Two main kinds of schedulers
    - **Conservative** - favours delaying operations
    - **Aggressive** - favours rejecting operations
    
### Two Phase Locking

- Transactions must have a lock on objects before access

- **Shared lock** - required to read an object

- **Exclusive lock** - required to write an object

- A transaction has to _acquire_ all locks before it _releases_ any of them

- **Theorem**: Two-phase locking guarantees that the produced transaction schedules serializable

**STRICT 2PL** - locks held till commit; guarantees ACA


### Deadlocks

- **Deadlock Prevention**
    - Locks granted only if they can't lead to a deadlock
    - Ordered data items and locks granted in this order
    
- **Deadlock Detection**
    - Wait for graphs and cycle detection
    - Resolution: the system aborts one of the offending transactions
    
### Different Locks

- **Multi-granularity locking**
    - Not all locked bojects have the same size
    - Advantageous in presence of bulk vs. tiny updates
    

- **Predicate locking**
    - Locks based on selecrtion predicate rather on a value
    

- **Tree locking**
    - Tries to avoid congestion in roots of B-trees
    - Allows relaxation of 2PL due to tree structure of data
    
### Inserts and Deletes

- Plain 2PL does not handle variable sets of data

- This is called the **phantom problem**

- **Solution**: operations that ask for all records have to lock against insertion/deletion of a qualifying record
    - Locks on tables
    - Index locks
    
### Isolation Levels

**Level 3** - serializability
    - Table-level strict 2PL
 
       
**Level 2** - repeatable read
    - Tuple-level strict 2PL
    
    
**Level 1** - cursor stability
    - Tuple-level exclusive-lock only strict 2PL
    - Reading the same object twice
    
**Level 0**
    - Neither read nor write locks are required
    - Transaction may read uncommitted updates
    
### Recovery: Goals and Setting

1. Allow transactions to be
    - Committed (with a guarantee that the effects are permanent)
    - Aborted (with a guarantee that the effects disappear)
    
    
2. Allow the database to be recovered to a consistent state in case on HW/power/... failure


### Approaches to Reovery

#### Shadowing
    - Copy-on-write and merge-on-commit approach
    - Poor clustering
    - Used in system R, but not modern systems
    
    
#### Logging
    - Use of LOG to avoid forced writes
    - Good utilization of buffers
    - Preserves original clusters
    
    - A **log** is a read/append only data structure
    - Transactions add logs records about what they do
    

- Log records
    - UNDO information
    - REDO information
    - BEGIN/COMMIT/ABORT
    
### Write-Ahead Logging (WAL)

- Make sure LOG is consistent with the main database

- Requires
    - **UNDO rule** - a log record for an update is written to log disk before the corresponding data is written to the main disk
    
    - **REDO rule** - all log records for a transaction are written to log disk before commit