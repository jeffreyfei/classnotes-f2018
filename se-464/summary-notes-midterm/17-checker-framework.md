# Checker Framework

- Java's type system is weak

### Pluggable Type checking

1. Design a type system to solve a specific problem
2. Write type qualifiers in code
3. Type checkers warns about violations

### Optional Type Checking

![](/assets/Screenshot from 2018-12-09 13-24-37.png)

### Static Type System

- Plug-in to the compiler


- Doesn't impact
    - Method binding
    - Memory consumption
    - Execution
    
### Benefits of Type Systems

- Find bugs in programs
- Improve document
- Aid compilers, optimizers, and analysis tools


- Possible negatives
    - Must write the types
    - False positives are possible
    
### The checker Framework

- A framework for pluggable type checkers

- Guarantees the program satisfies the type property