# Finals Summary Notes

### Blocking Locks

- Acquiring task makes one check for open locks and blocks
- Releasing task has sole responsibility for detecting blocked acquirer and transferring lock or just releasing lock

### Mutex Lock

- Solely for mutual exclusion

- **Single acquisition** - Task that acquired the lock cannot acquire it again
- **Multiple acquisition** - Lock owner can acquire it multiple times, called **owner lock**

- Acquiring tasks can barge ahead of released task
- Released task must check again => busy waiting

### Barging Avoidance

- Hold a flag variable between releasing and unblocking task
- The idea is that although barging still occurs, the program will put the barging task onto the blocked queue

- **Continuous barging** can occur, which leads to starvation as released task waits to reacquire lock

### Barging Prevention

- Hold lock between releasing and unblocking task
- The idea is never release the lock
- The releasing task remove blocked task from the ready queue without releasing the lock, unless the blocked queue is empty

#### uOwnerLock

- Multiple acquisition mutex lock
- `owner()` returns nullptr if no owner, otherwise address of current owner
- `times()` returns the number of times locks has been acquired by the owner task
- Must release as many times as acquire

### Stream Locks

- Specialized mutex locks for I/O based on uOwnerLock

**Syntax:**
`osacquire(cout) << "abc" << edf << endl;`

`isacquire(cin)` - for input streams

- e.g. Constraining output of async tasks to different lines

### Synchronization Lock

- Soley to block tasks waiting for synchronization

- _Acquiring task always blocks_
- _Release is lost when no waiting task_

- Also called **condition lock**

- **External locking** - use an external lock to protect task list
    - Avoid lost release
    
    
- **Internal locking** - use an internal lock to protect state

#### uCondLock

- `empty()` returns false if there are tasks blocked on the queue and true otherwise

- `wait()` and `signal()` are used to block a thread and unblock a thread from the queue of a condition, respectively
    - wait atomically blocks the calling task and releases the argument owner-lock
    - wait reacquires its argument owner-lock before returning
    
### Barrier

- coordinates a group of tasks performing a concurrent operation surrounded by sequential operations

- Blocks tasks until the blocked tasks reaches a certain number
- Tasks leaves synchronized after arriving at the barrier


##### Syntax
- `Barrier b(3)`

- Blocks 3 tasks before releasing
- `_Cormonitor` can inherit from `public uBarrier()`

### Binary Semaphore

- 0 - closed, 1 - open
- Default to 1

`BinSem lock(1)` - initialize
`lock.P()` - acquires
`lock.V()` - release

### Counting Semaphore

- `P()` decrements the counter
- `V()` increments the counter


- Blocks when counter is currently less than or equal to 0 before acquiring
- Negative counter indicates the number of waiting tasks

### Precedence Graph

- Displays dependencies on of blocks of code