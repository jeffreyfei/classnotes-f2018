### Ex. 2.8

![](/assets/Screenshot from 2018-09-18 11-41-01.png)

- When E5 is thrown, it searches through B6 to see if there's a handler, but there is none in B6.
- B5 has no handler
- It finds C5 in B4, and there's a match, the exception is caught.
- C5 throws exception, it continues onto C7, and gets caught at C8

### Difference between uC++ and C++ in throw
- In C++ the base class is thrown even when a derived class is passed in
- In uC++ the derived class is thrown
- Check **page 22** in the notes for more details

**The resumption handler** cannot perform a break, continue or return
    - Since it's a corrective actions so computation can continue
    - Should throw an exception if correction is not possible
    
### Coroutine

- A coroutine has it's own stack to cache information in order to resume after the context switches back to itself
- Coroutine is sequential (not concurrent)
- A coroutine can be terminated in suspension, but it has to be responsible to clean up everything on the stack by calling all the destructors