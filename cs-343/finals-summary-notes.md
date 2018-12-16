# Finals Summary Notes

## Some Execution Properties

![](/assets/Screenshot from 2018-12-15 23-30-28.png)

## Some Syntax

`_Accept(member1, member2, ...)`
`When(cond) _Accept(..)` - Condition for the critical region, works like if
`_Accept(mem1) or _Accept(mem2)` or condition for accept, unblocked if one of the member is called
`_Accept(mem1) {} _Else{}` - executes Else if no task waiting to be accepted

## Locks

### Blocking Locks

* Acquiring task makes one check for open locks and blocks
* Releasing task has sole responsibility for detecting blocked acquirer and transferring lock or just releasing lock

### Mutex Lock

* Solely for mutual exclusion

* **Single acquisition** - Task that acquired the lock cannot acquire it again

* **Multiple acquisition** - Lock owner can acquire it multiple times, called **owner lock**

* Acquiring tasks can barge ahead of released task

* Released task must check again =&gt; busy waiting

### Barging Avoidance

* Hold a flag variable between releasing and unblocking task
* The idea is that although barging still occurs, the program will put the barging task onto the blocked queue

* **Continuous barging** can occur, which leads to starvation as released task waits to reacquire lock

### Barging Prevention

* Hold lock between releasing and unblocking task
* The idea is never release the lock
* The releasing task remove blocked task from the ready queue without releasing the lock, unless the blocked queue is empty

#### uOwnerLock

* Multiple acquisition mutex lock
* `owner()` returns nullptr if no owner, otherwise address of current owner
* `times()` returns the number of times locks has been acquired by the owner task
* Must release as many times as acquire

### Stream Locks

* Specialized mutex locks for I/O based on uOwnerLock

**Syntax:**  
`osacquire(cout) << "abc" << edf << endl;`

`isacquire(cin)` - for input streams

* e.g. Constraining output of async tasks to different lines

### Synchronization Lock

* Soley to block tasks waiting for synchronization

* _Acquiring task always blocks_

* _Release is lost when no waiting task_

* Also called **condition lock**

* **External locking** - use an external lock to protect task list

  * Avoid lost release

* **Internal locking** - use an internal lock to protect state

#### uCondLock

* `empty()` returns false if there are tasks blocked on the queue and true otherwise

* `wait()` and `signal()` are used to block a thread and unblock a thread from the queue of a condition, respectively

  * wait atomically blocks the calling task and releases the argument owner-lock
  * wait reacquires its argument owner-lock before returning

### Barrier

* coordinates a group of tasks performing a concurrent operation surrounded by sequential operations

* Blocks tasks until the blocked tasks reaches a certain number

* Tasks leaves synchronized after arriving at the barrier

##### Syntax

* `Barrier b(3)`

* Blocks 3 tasks before releasing

* `_Cormonitor` can inherit from `public uBarrier()`

### Binary Semaphore

* 0 - closed, 1 - open
* Default to 1

`BinSem lock(1)` - initialize  
`lock.P()` - acquires  
`lock.V()` - release

### Counting Semaphore

* `P()` decrements the counter
* `V()` increments the counter

* Blocks when counter is currently less than or equal to 0 before acquiring
* Negative counter indicates the number of waiting tasks

### Precedence Graph

* Displays dependencies on of blocks of code

### Unbounded Buffer

* Two task communicate through a queue of unbounded length

* Producer never has to wait as buffer has infinite length
* Consumer has to wait if buffer is empty - wait for producer to add

### Bounded Buffer

* Two tasks communicate through a queue of bounded length

* Producers has to wait if buffer is full \(wait for consumer to remove\)
* Consumer has to wait if buffer is empty \(wait for producer to add\)

### Lock Techniques

#### Split Binary Semaphore

* A collection of semaphores where at most one of the collection has the value 1

#### Baton Passing

1. There is exactly one (conceptual) baton
2. Nobody moves in the entry/exit code unless they have it
3. Once baton is released, cannot read/write variables in entry/exit


- Mutex lock cannot use baton passing to prevent barging
  - Signalled task must implicitly reacquire lock before continuing
    - Signaler must release the lock
  - There is now a race between signalled and calling tasks

- Dekker's solution solves fairness on simultaneous arrival
  - Done by alternation
  - First select from opposite kind on exit
  
## Concurrent Errors
### Race Condition
- Occurs when there is missing _synchronization_ or _mutual exclusion_

### Deadlock

##### Must Occur:
1. A concrete shared-resource requiring mutual exclusion
2. A process holds resource while waiting for access to a resource held by another process
3. Once a process has gained access to a resource, the runtime system cannot get it back
4. There exists a circular wait of processes on resources
5. These conditions must occur simultaneously


- Deadlock can be prevented by removing one or more of these conditions

1. No mutual exclusion
  - Not possible sometimes
2. No hold and wait
  - Poor resource utilization
  - Possible starvation
3. Allow preemption
  - Cannot apply statically
4. No circular wait
  - Control the order of resource allocation
  - Use an _ordered resource policy_
5. Prevent simultaneous occurrence

##### Ordered Resource Policy

- Divide resources into classes $$R_1, R_2, R_3$$
- Can only request resource from that class if not holding resource in the same class or higher
- Requires requesting several resources simultaneously unless each class contains only one resource
- $$h(T)$$ - the highest class number for which $$T$$ holds a resource
- If $$T_1$$ is blocked by $$T_2$$ for resource class $$k$$ then $$h(T_1) < k \leq h(T_2)$$
  - Circular wait is impossible in this case


- Does not always work optimally. May result in poor resource utilization in some case

### Deadlock Avoidance

- Monitor all lock blocking and resource allocation to detect potential deadlock
- Better resource utilization but more overhead

### Banker's Algorithm

- Computes safe allocations of resources
- Requires a process to state its maximum resource needs

### Allocations Graphs

![](/assets/Screenshot from 2018-12-15 22-19-20.png)

![](/assets/Screenshot from 2018-12-15 22-18-41.png)

- No cycle => no deadlocks
- If a resource has multiple instances, then a cycle is not a deadlock

### Deadlock Recovery

- One strategy can be letting deadlocks happen then recover from it
- Requires preemption of one or more process in the cycle
  - Must not create starvation
  - The victim must be restarted
  
## Indirect Communication

### Monitor
- An abstract data type that combines shared data with serialization of its modification

- **Mutex member** - does not begin execution if there is another active mutex member
  - Can be blocked on entry into a waiting queue
  - Public members of a monitor is implicitly a mutex member, other members can be explicitly declared as a mutex member
- Exceptions within a monitor always release implicit monitor locks
- Destructor is mutex, therefore deleting a dynamically allocated monitor will block if there exists an active thread in the monitor
  - Useful for termination detection
  
### Scheduling
- There are two techniques for scheduling

##### General Model of Monitor Members
![](/assets/Screenshot from 2018-12-15 23-38-33.png)

#### External
  - schedules tasks outside the monitor; accomplished using the `_Accept` statement
  - the `_Accept` statement controls which mutex member can accept calls
  

  - A queue of tasks blocks outside the monitor waiting to be accepted
  - The acceptor blocks until a call to the specified mutex member occurs
    - Can form a stack of blocked acceptors
  - Acceptor resumes when the mutex member exists or gets blocked
  
#### Internal
  - schedules tasks inside the monitor; accomplished using condition variables (signal / wait)
    - A condition is a queue of waiting tasks
    
  - `empty()` - returns true of the queue is empty; false otherwise
  - `wait()` - the current task blocks
  - `signal()` - Unblocks the task in front of the waiting queue
    - Does not block
    - The waiting task is unblocked after the signaler thread blocks or exists
  - `signalBlock()` - Same as `signal()` but blocks the signaler when called
    - Allowing the waiting task to execute first
    
#### Summary
- External is generally easier to use, but cannot be used if
  - Scheduling depends on a member parameter value
  - Scheduling must block in the monitor but cannot guarantee the next call fulfils cooperation
  
- **Nested monitor problem** - acquire monitor $$M_1$$, call to monitor $$M_2$$ and wait on a condition in $$M_2$$
  - Condition in $$M_2$$ is released by wait, but monitor lock in $$M_1$$ is not released. Potential deadlock.
  
- Differences to a counting semaphore
  - `wait()` always blocks, not the case for `P()`
  - `signal()` can be lost if nothing is waiting on the condition, not the case for `V()`
  - Multiple `V()` starts tasks simultaneously while multiple `signal()` does not
    - As each task must exit serially through the monitor
  
### Monitor Types

 ![](/assets/Screenshot from 2018-12-15 23-09-32.png) 
 
 - Either explicit or automatic signal
 - Has waitUntil _condition_
 
#### Other Types and Priorities
 
 ![](/assets/Screenshot from 2018-12-15 23-12-51.png)
 
##### No-priority blocking
 - Signaller task recheck the waiting condition for barging task
 - While loop around signal
 
##### No-priority non-blocking
 - Signalled task recheck the waiting condition for barging task
 - While loop around wait
 
##### Implicit Signal (automatic)
 - Good for prototyping but poor performance
 
##### Priority non-blocking
 - No barging
 - Optimizes signal before return
 
##### Priority blocking
 - No barging
 - handles internal cooperation within the monitor
 
### Cormonitor
 
 - Same as monitor, but has a `main()` function and can use `resume()` and `suspend()`
 
### Java Monitor

- Java has synchronized class members and a synchronized statement (mutex members)

- Internal scheduling is no-priority non-blocking => barging

## Direct Communication

### Task
- Has `main()` with its own execution state
- Has a thread of control
  - `main()` executes immediately after the task's creation
- Provides mutual exclusion like a monitor
  - Only one active thread within the object at a time
  - Public members are implicitly mutex
  - External scheduling allows direct call to mutex members
  
### Scheduling

#### External
- Can use `_Accept()` like monitors

- **Exceptions** in a task member propagates to the caller

#### Internal
- `wait()` and `signal()` are used like monitors

#### Accepting Destructor
- A common way to stop tasks (e.g. when you have an infinite loop in `main()`
- by deleting the task object, it calls the destructor, which will be accepted


- When the destructor is called, the caller is blocked
- When the destructor is accepted, the caller is blocked and moved to the A/S stack instead of the acceptor
  - Control returned to the accept statement instead of the destructor member
  - Allows mutex to cleanup before termination
  
### Increase Concurrency

#### Client-server

- The server is a task with a running `main()` function
- Clients are tasks that calls the member functions of the server

- We should try to put as much work in the `main()` function as possible instead of within the member functions
  - Since mutex members block, by doing less work, we allow more clients to access the member functions
  
#### Internal Buffer

- The requests from clients can be inserted into an internal buffer
- We know that no members can be called when the server is working
- Add a worker thread to get work from the buffer and return results to the buffer
  - Multiple works is also possible
    - Balanced with the number of clients to maximize concurrency (bounded buffer problem)
    
#### Administrator

- A server managing multiple clients and worker tasks
- Does little to no work
- Called by others
- Keeps a buffer of work to pass to the worker tasks

##### Kinds of Workers

- **Timer**
- **Notifier** - performs potential blocking wait for an external event
- **Simple worker** - receive work and return result to admin
- **Complex worker** - receive work and interact directly with client
- **Courier** - Perform potentially blocking call for the admin

##### Client
- Sometimes the client does not have to wait for the server to process a request
  - Can be performed via an async call to the server
  - Requires a implicit buffer to store the arguments of the call

##### Returning Values
- Must be split into two calls

```
callee.start(args);
// do something

result = callee.wait();
```

- In the assignment this is done by returning a future

**Some techniques**:

- **Tickets** - the caller passes in the ticket to retrieve the result
  - Result is stored in some kind of data structure
  - Caller may not obey the protocol (passing in bogus ticket)
  
- **Callback routine** - register a routine in the initial call
  - The routine is called with the result when the work is complete
  
- **Futures** - an data structure that provides asynchrony required in this problem
  - When the future is not fulfilled (work not completed), think of it as a phony value to make the caller thinks that the call is completed
  - When the caller tries to obtain results from an empty future, the caller blocks
  - When the result is calculated, then the future is fulfilled by the callee. As soon as this happens, the caller gets unblocked
  
##### UC++ Implementation of futures

`Future_ESM<T>` - must be allocated and deallocated by the client
`Future_ISM<T>` - automatically allocates and deallocates storage

`Future_ISM<int> f; f();` - try to access result, blocks if not available
  - Raise exception if exception raised by server
`available()` - true if results available; false otherwise
`reset()` - mark future as empty
`cancel()` - cancels the async call that the future refers to
`cancelled()` - true if the future is cancelled; false otherwise


`_Select(future) {}` can be used to wait on future access
  - Executed when future becomes available, blocks otherwise
  - Functions similarly to `_Accept()`
  - Can be used in conjunction with `or`, `_Else{}`, `_When()`, `and`
  
## Optimization

#### General Forms for Optimization

- **Reordering** - data and code are reordered increase performance in certain contexts
- **Eliding** - removal of unnecessary data, data accesses, and computation
- **Replication** - processors, memory, data, code are duplicate because of limitation in processing and communication speed

- Optimized program must be _isomorphic_ to original => produce same result for fixed input

### Sequential Optimization

1. Reorder disjoint (independent) operations
2. Elide unnecessary operations
3. Execute in parallel if multiple functional units

### Memory Hierarchy

#### Caching

- Move data from memory to registers for as long as possible and back to memory
- Compilers try to keep highly accessed data in registers
- Use hardware cache to stage data without pushing to memory and allow sharing of data among programs

- **Cache line** - the size of the block that cache can load data (64/128/256)

#### Cache Coherence
- **Cache coherence** - hardware protocol ensuring update of duplicate data
  - Since variable data can be replicated in a large number of locations
  
  
  
- **Cache consistency** - addresses when processor sees update => bidirectional synchronization
  - **Eager data consistency** - data changes appear instantaneous by waiting for acknowledge from all cores
  - **Lazy data consistency** - reader to see own write before acknowledgement
  
  
- **Cache thrashing** - excessive cache updates caused by continually read/write the same memory locations
- **False sharing** - when thrashing occur inadvertently due to multiple variables using the same cache line


### Concurrent Optimizations

- Sequential sections accessing private variables can be optimized normally but not across concurrent boundaries

#### Disjoint Reordering

- Orders of operations that are disjoint can be altered
- Compilers uses the technique to break mutual exclusion
  - e.g. Move lock entry/exit after/before critical section because entry/exit variables not used in critical section
  
#### Eliding

- Elide reads by replicating value into register
- Variable logically disappears for duration in register
  - Since reading directly from register is more efficient

#### Replication

Processor Execution Steps:

1. Internal pool of instructions taken from program order
2. Begin simultaneous execution of instructions with inputs
3. Collect results from finished instructions
4. Feed results back into instruction pool as inputs
5. Instructions with independent input execute out of order

- **Double-check locking** - check the same condition before and after acquiring the lock


### Optimization Problems

- Locks effect efficiency
  - Locks define the sequential/concurrent boundaries
  - Boundaries must preclude optimizations that affect concurrency
  
  
- **Race free** - when synchronization and mutual exclusion preclude races


- Two approaches
  - **Adhoc** - manually augments all data races with pragmas to restrict compiler/hardware optimizations
    - Not portable but often optimal
  - **Formal** - language has memory model and mechanisms to abstractly define races in program
    - Portable but often suboptimal
    
    
- `volatile` qualifier in C/C++
  - Force variable loads and stores to registers (At sequence points)
