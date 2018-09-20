## Coroutine

- We can suspend and resume coroutines without destroying it's information, as it is saved on the coroutine's stack

### Ex. 3.1.2

#### 3.1.2.2
- Global variables *a*, *b* to remember where you are

#### 3.1.2.4
- By having `resume()` in the constructor. It make sure that the developer has the control of starting the coroutine

### Correct Coroutine Suage

- Eliminate computation or flag variables retaining formation about execution state

![](/assets/Screenshot from 2018-09-20 12-00-02.png)

- Can eliminate the `if` check since we know that odd and even numbers comes in an alternate pattern

### Coroutine Construction
#### Memory Management
- There's a guard page at the end of the stack, which will return a seg. fault when the stack overflows

## Nonlocal Exceptions

- Exception raised by a source execution at a faulting execution
- You need to resume the coroutine before throw the exception to the coroutine