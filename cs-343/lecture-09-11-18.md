### Flag Variables
- Eliminate flag variables necessary with while
    - They are the variable equivalent to a goto
    
- Labelled exit variables are essentially goto
- Occasionally a flag variable is necessary

### Good vs. Bad Goto

- Only forward branching
    - It should not create a loop in the program
    - Cannot branch into a control structure    
- Only use goto to perform static multi-level exit, e.g. simulate labelled break and continue

- Continue statements branches down

### Dynamic Memory Allocation
- Use the stack if you can

```cplusplus
// GOOD
cin >> size;
int arr[size];
// use arr[i]
```
vs.
```cplusplus
// BAD
cin >> size;
int * arr = new arr[size];
// use arr[i]
delete [] arr;
```

Use the heap when:

1. A variable's storage must outlive the block in which it is allocated
2. When the amount of data read is unknown (e.g. a vector)
3. When an array of objects must be initialize via the object's constructor
4. When large local variables are allocated on a small stack

### Dynamic Multi-Level Exit

- **Modularization**: any contiguous code block can be factored into a routine and called form anywhere in the program

- Many routines have *multiple outcomes*
    - Normal: return normal result and transfer after call
    - Exceptional: return alternative result and not transfer after call
    
```fortran
subroutine AltRet(c, *, *)
    integer c
    if (c == 0) return !normal return
    if (c == 1) return 1 !alternate return
    if (c == 2) return 2 !alternate return
    
AltRet(1, *10, *20)
```
- Dynamic multi-level exit extend call/return semantics to transfer in the reverse direction to normal routine calls, called *nonlocal transfer*

- Transfer between goto and label value causes termination of stack block

### Traditional Approaches

- **Return code** - returns value indicating normal or exceptional execution
- **Status flag** - set shared variable indicating normal or exception execution; the variable remains as long as it is not overwritten
- **Fix-up routine** - a global and/or local routine called for an exceptional event to fix-up and return a corrective result so a computation can continue

Drawbacks:
- Nonlocal return code or status flag testing is difficult
- Status flags can be overwritten
