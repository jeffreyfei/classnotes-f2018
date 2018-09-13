## Continuation from last Lecture
- Review on traditional approaches, see notes from last lecture

![](/assets/Screenshot from 2018-09-13 11-42-57.png)

- `g()` doesn't do any forwarding
- For instance, we can also pass `f` to `g` as a fixup routine, in which case `g` does not need to have any knowledge of how `f` works

- Note: the goto line on the left is *outdented* to improve readability

- This is exception handling

## 2.2 Exception Handling

- Dynamic multi-level exit allows complex forms of transfers among routines
- Complex control-flow among routines is often called *exception handling*

- **Exception** != **Error**
    - It just implies alternate outcomes, which can be error or other stuff

- Hard to simulate with simpler control structures (ugly code)    

## 2.3 Execution Environment

- C++ makes sure that the destructor is called regardless of the outcome

- Finally blocks is useful in this case to ensure a behaviour to always happen
    - `_Finally` in $$\mu$$C++
    
- All of this works with the stack (e.g. going from point F to G on the stack)
    - What happens if there are multiple stacks?
        - Continue propagating the exception in another stack
        
## 2.4 Terminology
- See course notes

- The rules for walking the stack (when propagating an exception) can vary from language to language

## 2.5 Static/Dynamic Call/Return

![](/assets/Screenshot from 2018-09-13 12-12-57.png)

e.g.
- The destination of a call to a method can be determined by examining the code, it is static
- The return of a routine is not deterministic by examining the routine, it can only be known when the code executes. It is dynamic

- Routine pointer's destination is not deterministic statically, it is dynamic

## 2.6 Static Propagation (Sequel)

- Example of a static return can be a label breaks, since labels are constants, therefore the return location is deterministic

- **Sequel** is a routine with no return value
- Control returns to the end of the block in which the sequel is declared
    - When it's called, it unwinds the stack

- Doesn't generalize since the return location is a constant
    - Hence can't be used for exception handling
    
## 2.7 Dynamic Propagation

![](/assets/Screenshot from 2018-09-13 12-38-41.png)
- Note that the code on the right and left does the same thing

- `throw` is a dynamic return
- `catch` block is static return (since it just moves onto the next line after execution)