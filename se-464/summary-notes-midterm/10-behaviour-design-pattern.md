![](/assets/chart.png)

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