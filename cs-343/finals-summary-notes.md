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