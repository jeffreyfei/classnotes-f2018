# Dependency Injection

#### SOLID Principles

- Single Responsibility
- Open/Closed
- Liskov Substituiton
- Interface Segregation
- Dependency Inversion


#### Dependency Inversion

- Higher level modules should depend on abstraction
- Abstractions should not depend on details
- Minimize direct coupling between concrete classes

##### Google Guice

- A common IoC framework
- Bind types of classes to their concrete implementation
- Use @Inject to automatically instantiate the correct objects

#### Inversion of Control (IoC)

- A design principle in which custom-written portions of a computer program receive the flow of control from a generic framework

##### Implementation Techniques

- Factory pattern
- Service locator pattern
- Dependency injection
- Template method design pattern
- Strategy design pattern

#### Goals of DI

- Eliminate intialization statements

##### How DI Works on a high level
- Takes a set of components
- Adds a set of configuration metadata
- Provides the metadata to an injection framework
- Boostraps object creation with a configured injector