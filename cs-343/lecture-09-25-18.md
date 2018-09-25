### Nonlocal Exceptions

- Normally when the exception can't find a handler after searching the stack, it will
    - Call default resume
    - Call default terminate
    
    
- Coroutines in ucpp this case will go to the last resumer
    - Potential recovery action
    

- Coroutine failures are always enabled (don't need to wrap the code in a Enable block)

# Full Coroutines

- Defined as allowing cycles in the control flow

![](/assets/Screenshot from 2018-09-25 12-12-37.png)

- Note this example
    - The program enters the coroutine by `fc.mem();`
    - `main()` of Fc calls `mem()`
    - Note that when `mem()` calls `resume()` again, it steps off the stack of `fc` and it resume the stack of `fc`. This creates a cycle in the coroutine, which makes this coroutine a full coroutine.
    
- Can be seen from this diagram

![](/assets/Screenshot from 2018-09-25 12-21-58.png)


