- More example walk throughs

## Coroutine Languages

- **Stackless** - use the caller's stack and a fixed-size local-state
- **Stackful** - separate stack and a fixed-size local -state

# 4 More Exceptions
## 4.1 Derived Exception-type

- A mechanism for inheritance of exception types
- Polymorphism among exception types
    - Generic exception types can catch less generic exception types
    
    
- Should always catch exception by reference

- Catch-any is a mechanism to match any exception propagating through a guarded block