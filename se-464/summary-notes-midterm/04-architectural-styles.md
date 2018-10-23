### Architectural Patterns
- A set of architectural design decisions that are applicable to a recurring design problem, and parameterized to account for different software development contexts in which that problem appears

### Three-Tiered Pattern

- **Front Tier**
    - Contains the user interface functionality to access the system's services
    
    
- **Middle Tier**
    - Contains the application's major functionality
    
    
- **Back Tier**
    - Contains the application's data access and storage functionality
    
### Architectural Style

- A named collection of architectural design decisions
- Family of architectures
- Improves design/code reuse, organization, interoperability, visualizations etc.

### Layered Style

- Hierarchical system organization
- Each layer acts as a
    - Server - service provider to layers "above"
    - Client - service consumer of layer(s) "below"

##### Example
- Operating systems
- Virtual machine

|Advantages|Disadvantages|
|---|---|
|- Increased abstraction levels|- Not universally applicable|
|- Evolvability| - Performance|
|- Change in a layer effect at most the adjacent two layers||
|- Different implementations of layers||
|- Standardized layer interface||

### Client-Server Style
- **Components**: clients and servers
- **Connectors**: RPC-based network interaction protocols
- Servers don't know the number or identities of client
- Client knows server
![](/assets/Screenshot from 2018-10-22 20-28-15.png)

### Data-Flow Styles: Batch Sequential

- Separate program executed in order
- Data is passed as an aggregate from one program to the next

- **Connectors:** - human hand, carrying tapes between programs

- Typically used in transaction processing in financial systems

### Pipe and Filter Style

- **Components:** filters
- **Connectors:** pipes

- Ex. piping in Linux shell


### Blackboard Style

**Components:** central data structure (blackboard), components operating on the blackboard

- System control entirely driven by the blackboard state

- Used for AI systems, integrated software environments, compilers etc.

### Rule-based Style

- Inference engine parses user input and determines whether it is a fact/rule or a query

- Adds fact/rule to the knowledge base, otherwise queries knowledge base for applicable rules and attempts to resolve the query

- When involved with large number of rules understanding interactions may be difficult

### Interpreter Style

- Interpreter parses and executes input commands, updating the state maintained by the interpreter

- **Components:** command interpreter, program/interpreter state, user interface etc.
- **Connectors** - very closely bound with direct procedure calls and shared state

- Highly dynamic behaviour
- Superb for end-user programmability

- e.g. Lisp and Scheme

### Implicit Invocation Styles

- Event annoucement instead of method invocation
    - Listeners register interest and associate methods with events
    - System invokes all registered methods implicitly
    

### Publish-Subscribe Style

![](/assets/Screenshot from 2018-10-22 21-53-40.png)

### Event-based Style
![](/assets/Screenshot from 2018-10-22 21-54-19.png)

### Peer-to-Peer Style

- **Components:** peers, with their own state and control thread
- **Connectors:** Network protocols, often cusom
- **Data Elements:** Network messages

### Distributed Objects: COBRA

- **Components: ** Objects, which epses services through well-defined provided interfaces
- **Connector:** Method invocation
- **Data Elements:** Arguments to methods, return values, and exceptions
- **Topology:** General graph of objects from callers to callees

**Design Recovery** - recover architecture from a system with no documentation
    - Examine code base
    - Determine components, connectors, topology etc.
    
##### Syntactic Clustering
- Focuses exclusively on the static relationship among code-level entities
- Can be performed without running the system
    
##### Semantic Clustering
- Includes all aspects of a system's domain knowledge
- Needs to interpret the system entities' meaning
- May need to determine at runtime