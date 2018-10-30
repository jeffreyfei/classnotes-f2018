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

### Barging Avoidance

### Barging Prevention