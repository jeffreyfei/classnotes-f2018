## 4.2 Catch-any

- Catching any reception through a guarded block

## 4.3 Exception Parameters

- Allows passing information from the raise to a handler

## 4.4 Exception List

- Specifies which exception types may propagate from the routine to it's caller


## 4.5 Destructor

- Destructor can raise exceptions
    - Requires the `noexcept(false)` keyword when defining the destructor
    
- It's undesirable to raise exceptions in a destructor


- A destructor *cannot* raise an exception during propagation
    - Since exception propagation requires the *unwinding of the stack*, in which case the destructors on the stack are called during the process. When the destructor raises an exception in this case it's raising a *second exception* before the first one is handled.
    
## 4.6 Implementation

- Raising an exception in C++ is expensive
    - Complicated algorithms has to be ran to generate tables which dictates where the exception has to go
    
## 5 Concurrency

**Parallel execution** - when 2 or more operations occur simultanenosly
    - Can only occur with multi-core CPUs
    

**Concurrent execution** - any situation in which execution of multiple threads *appears* to be parallel
    - A concurrent program can become parallel when executed on a computer with multiple CPU cores
    
## 5.3 Concurrent Hardware

- Task switching may occur at **non-deterministic** program locations