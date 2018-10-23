**Composition** - Creating objects with other objects as members
    - Should be used when a has-a-relationship applies
    
**Inheritance** - The concept of classes automatically containing the variables and methods defined in their supertypes

- Composition >> Inheritence

**Creational Patterns** - Defer decision about class instantiations until runtime

### Overview

![](/assets/Screenshot from 2018-10-23 01-29-19.png)

**Flyweight Pattern**
- Use sharing to support large number of related objects
- When a new object is requested, the factory tries to find an existing object that satisfies the requirement, if there isn't one then a new object is created