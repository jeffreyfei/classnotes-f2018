# Checker Framework

- Also includes 18, Part 2

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

### Optional/Gradual Type Systems

- TypeScript
- Flow
- Python 3

### Newer PLs

- Scala
- Kotlin
- F#
- Swift
- Julia
- Reason

### Some Checker Syntax

@Regex
- Valid regular expression

@Regex(2) - two capturing groups

@NonNull - a non-null reference to data

@Interned - an interned string (one instance)

@English - an English string

- Need library spec when annotating external libraries


##### Facilities

- Full tyep system
- Generics
- Qualifier defaults
- Pre-/post-conditions
- Warning supression

##### Nullness Checker

Prevent: NullPointerException

Hold: @NonNull references always non-null

Legal: Dereferences only on @NonNull References

##### Regex Checker

Prevent: PatternSyntaxException

Hold: A string is a regex and number of groups

Illegal: Pattern.compile with non regex


##### Defining a Type System

1. Qualifier hierarchy
    - Defines subtyping

2. Type introduction rules
    - Types for expressions
    - How a type is initializeda

3. Type rules
    - Checker-specific errors
    
4. Flow-refinements
    - Better types than the programmer wrote
    
### Dataflow Framework

Goal: Compute properties about expressions
    - More accurate types than the user wrote

Dataflow framework user provides
    - What are we tracking
    - What do operations do
    - What are intermediate results