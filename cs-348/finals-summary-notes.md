# Finals Summary Notes

## Normal Forms

#### 1NF
- Column of a table cannot hold multiple values
- Only hold atomic values

#### 2NF
- Table is in 1NF
- If a candidate key has multiple attributes, then part of that candidate key cannot determine anything

    e.g.
    
    AB -> C
    A -> D
    B -> E
    
- We can see that in this case AB is a candidate key, however subset in AB is used to determine other attributes. Therefore the above relation is not in 2NF

#### 3NF

- No _transitive dependency_

#### BNCF

- In a non trivial relation X->Y, X must be a superkey

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
    
## Database Tuning

- **Physical Design** - the process of selecting a physical schema (collection of data structures) to implement the conceptual schema

- **Tuning** - periodically adjusting the physical and/or conceptual schema of a working system to adapt to changing requirements and/or performance characteristics

### Workload

- **Workload Description**
    - The most important queries and their frequency
    - The most important updates and their frequency
    - The desired performance goal for each query or update
    
    
##### Example

- Query
    - which relations are accessed
    - which attribute are retrieved
    - which attributes occur in selection/join conditions? how selective is each condition
    

- Update
    - Type of update and relations/attributes affected
    - Which attributes occur in selection/join conditions? How selective is each condition
    
    
### Tuning
- Make a set of application execute as fast as possible


### Overheads

##### Table Scan

- e.g. SELECT blocks will require DBMS to search the blocks of the database to find a match
- Assuming not sorted, all blocks of the file must be scanned if the entry is not found

##### Creating Indexes

- Substantially reduce execution time for selection
- Increase execution for insertions
- Increase or decrease execute time for updates or deletions
- Increase required space


##### Clustering vs. Non-clustering Indexes

-  relation may have at most one clustering index, and any number of non-clustering indices

##### Co-Clustering Relations

- Two relations are co-clustered if their tupes are interleaved within the same file

- Can speed up joins (particularly foreign key joins)
- Sequential scans of either relation become slower

##### Range Queries
- B-trees can help for range queries
    - Using forward pointers in the leaf blocks when finding the first qualifying entry
    
    
##### Multi-Attribute Indices

- It is possible to create an index on several attributes of the same relation

- e.g. `CREATE INDEX NamerIndex ON Employee(Lastname,Firstname)`

- order matters
- ordered first by Lastname, then Firstname

### More Complex Designs

##### Multi-Attribute Indices

- Complex search/join conditions
- Join indices
- Materialized views

##### Join indices

- Allow replacing joins by index looups

##### Materialized views

- Allow replacing subqueries by index lookups


### Physical Design Guidelines

1. Use index only if performance increase outweighs update overhead

2. Attributes mentioned in WHERE clauses are candidates for index search keys

3. Multi-attribute search keys should be considered when
    - A WHERE clause contains several conditions
    - Enables index-only plans
 
       
4. Choose indexes that benefit as many as queries as possible

5. Each relation can have at most one clustering theme; therefore choose it wisely
    - Target important queries that would benefit the most
        - Range queries benefit the most from clustering
        - Join queries benefit the most from co-clustering

    - A multi-attribute index that enables an index only plans does not benefit from being clustered
    
### Index Selection and Tools

- Convert physical design into another optimization problem

### Tuning Conceptual Design

- To avoid expensive operations in query execution
- Retrieve related data in fewer operations

##### Techniques

- Alternative normalization/weaker form
- Co-clustering of relations
- Vertical/horizontal partitioning of data
- Avoiding concurrency hot-spots


### Denormalization

- **Normalization** - the process of decomposing schema to reduce redundancy

- **Denormalization** - the process of merging schema to intentionally increase redundancy

- Redundancy increase update overhead but decreases query overhead

### Partitioning

- Splitting a table into multiple tables for the purpose of reducing I/O cost or lock contention

- **Horizontal Partitioning**
    - Each partition has all original columns and subset of original rows
    - Often used to separate operational from archival data
    

- **Vertical Partitioning**
    - Each partition has a subset of the original columns and all the original rows
    
    - Used to separate frequently used columns from each other
    
### Tuning Queries

1. Sorting is expensive. Avoid unnecessary uses of ORDER BY, DISTINCT or GROUP BY
2. Whenever possible, replace subqueries with joins
3. Whenever possible, replace correlated subqueries with uncorrelated subqueries
4. Use vendor-supplied tools to exmaine generated plan. update and/or create statistics if poor plan is due to poor cost estimation

### Tuning Applications

1. Minimize communication costs
    - Return the fewest columns and rows necessary
    - Update multiple rows with a WHERE clause 
    
2. Minimize lock contention and hot-spots
    - Delay updates as long as possible
    - Delay operation son hot-spots as long as possible
    - Shorten or split transactions as much as possible
    - Perform insertions/updates/deletions in batches
    - Consider lower isolation levels