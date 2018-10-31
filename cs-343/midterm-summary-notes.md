## Midterm Summary Notes

- **Multi-exit loop** - loops that has one or more exit locations within the body of the loop

- **Flag variable** - variables that is used solely to affect control flow
    - Equivalent to a goto
    
    
- **Static multi-level exit** - exists multiple control structures where exit points are known at compile time
    - Only use goto
    
- Stack allocation is often more efficient since it eliminates explicit storage management

- Use the heap when
    1. When a variable's storage must outlive the block in which it is allocated
    2. When the amount of data read is unknown
    3. When an array of objects must be initialized via object's constructor
    4. When large local variables are allocated on a small stack
    
- **Exceptions** - return alternative result and not transfer after call

- **Return union** - combines result/return code, and checks code on result access

#### Problems with Traditional Error Checking (Not Exception)
- Check return code or status flag is optional (can be delayed or omitted)
- Return code mixes exceptional and normal values
- Code difficult to read
- Nonlocal return code or status flag testing is difficult
- Status flag may be overwritten

- More complex EHM may be needed for OOP environments
- e.g. objects may have destructors that must be executed

#### Static / Dynamic Call / Return

![](/assets/Screenshot from 2018-10-30 03-49-17.png)

- **Sequel** - a routine with no return value
    - Returns at the end of block in which is sequel is declared
    - Handler is statically known
    - Works only for monolithic programs

        
- Dynamic propagation / static return is also called dynamic multi-level exit
    - Works for separately-compiled programs
    - Handler not statically known
    
##### Termination
- Control transfers from the start of propagation to a handler
- When handler return, it performs a static return (stack is unwound)

##### Resumption
- Control transfers from the start of propagation to a handler (dynamic raise)
- When handler returns, it is dynamic return (Stack not unwound)

- **In C++, if a derived type is passed in (polymorphism) as the base class the base class is thrown. In uC++ the derived class is thrown in the same situation**

- **Lexical link** - works like **this** but to declaration block rather than object

- **Resumption handler cannot perform a break, continue, or return**
    - Should throw exception if correction is not possible
    
##### defaultResume
- If no CatchResume is found, defaultResume is called, which rethrows the event, and the event will get caught by the next catch block (if it exists)

## Coroutine

- Has it's own stack and its local variables
- When deleted, a coroutine's stack is always unwound and any destructors executed
- Default coroutine stack size is 64K and does not grow
- Expands to next stack instead of heap
- Nonlocal exceptions are queued and delivered in FIFO order
    - Disabled by default in a coroutine
- Exception UnhandledException (and a few others) are always enabled

- **this** and `uThisCoroutine` changes at different times

### Coroutine Languages

- **Stackless** - use the caller's stack and a fixed-size local-state
    - Cannot call other routines then suspend (only suspend in the coroutine main)
    - Python, Ruby, JavaScript, C# etc.


- **Stackful** - separate stack and fixed-sized local-state

## More Exceptions

- **Derived exception types** - derived exception classes from a parent exception class
    - Can form a tree like exception hierarchy
    
- Destructor is implicitly noexcept => cannot raise an exception

- Cannot raise an exception during propagation

## Concurrency

- **Thread** - independent sequential execution  path through a program

- **Process** - a program component that has its own thread and has the same state information as a coroutine

- **Task** - similar to a process except that it is reduced along some particular dimension

- Concurrency is possible on uniprocessor with context switching

- **Task switching** may occur at non-deterministic program locations
    - Can happen explicitly (e.g. calling routines)
    - Can happen implicitly due to an external interrupt or timer
    
    
- Interrupt is **preemptive** if it affect scheduling (execution order)

#### Execution States

![](/assets/Screenshot from 2018-10-30 18-52-26.png)

running -> ready (timer alarm)
blocked -> ready (completion of I/O operation)
running -> halted (exceeding some limit e.g. CPU time, error)

#### Threading Model

- **kernel threads** - used by the OS to provide logical access to the CPU (virtual processors)
- A process may have multiple kernel threads to provide parallelism on multiple CPUs

##### Relationship between user:kernel:CPU

![](/assets/Screenshot from 2018-10-30 18-58-11.png)

- uC++ only has explicit concurrent mechanisms

#### Speedup From Concurrency

![](/assets/Screenshot from 2018-10-30 19-03-23.png)

##### Amdahl's Law

$$S_c=\frac{1}{(1-P)+P/C}$$

where $$T_1=1, T_C=sequential+concurrent$$

P - the concurrent section of the given program
- Goal is minimize the sequential part of the program

- Concurrent program is bound by the *critical path* of computation
    - Longest path bounds speedup
    
- **Independent execution** - all threads created together and do not interact
- **Dependent execution** - threads created at different times and interact

- Also affected by scheduler
    - Greedy scheduling, LIFO scheduling etc.
    
    
- **Critical section** - a group of instruction on an associated object that must be performed atomically

- **Mutual exclusion** - prevention of simultaneous execution of a critical section by multiple threads

- Need to minimize the size of critical section to maximize concurrency

- Avoid static variable in a concurrent program as it may be difficult to enforce mutual exclusion

#### 5 Rules of Mutual Exclusion

1. Only one thread can be in a critical section at a time with respect to a particular object
2. Threads may run at arbitrary speed and in arbitrary order, while the underlying system guarantees threads makes progress
3. If a thread is not in the entry or exit code controlling access to critical section, it may not prevent other threads from entering critical section
4. In selecting a thread to enter the critical section, the selection cannot be postponed indefinitely (livelock)
5. After a thread starts entry to the critical section, it must eventually enter (starvation)

##### Dekker's Algorithm

- **RW-safe** - works if simultaneous writes scramble bits and simultaneous read/write reads flickering bits

- Dekker's algorithm is not RW safe
- Hesselink version is RW safe

- Dekker'shas unbounded overtaking since race loser retracts intent

- Peterson's has bounded overtaking because race loser does not retracts intent

- Peterson's is RW-unsafe and requires atomic read/write


### Barging Avoidance

### Barging Prevention