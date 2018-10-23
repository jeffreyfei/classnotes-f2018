**Composition** - Creating objects with other objects as members
    - Should be used when a has-a-relationship applies
    
**Inheritance** - The concept of classes automatically containing the variables and methods defined in their supertypes

- Composition >> Inheritence

**Creational Patterns** - Defer decision about class instantiations until runtime

### Overview

![](/assets/Screenshot from 2018-10-23 01-29-19.png)

**Bridge Pattern** - Separate implementation and classes to avoid duplication of implementation in similar children classes

**Proxy Design Pattern** - Uses a wrapper (proxy) around the real component
- Dynamically initialize objects on demand of the client

**Composite Pattern**
- Creates a nested structure of leaf and component objects, component can be nested in another component, leaf can be nested in a component
- Can create a tree like pattern

**Flyweight Pattern**
- Use sharing to support large number of related objects
- When a new object is requested, the factory tries to find an existing object that satisfies the requirement, if there isn't one then a new object is created

**Visitor pattern** - Uses a visitor class to perform operations on an object
- Define new operation without changing the classes of the elements on which it operates
    - Create new visitor subclass
    
    
**MVP** - Model View Presenter
- Uses a presenter class (instead of controller) that glues the Model and the View together
    - Houses application logic
    - Updates View when Model changes, updates Model when user changes the View
- Same as MVC with improve decoupling of Views and Model
- Better Testability
- More complex than MVC