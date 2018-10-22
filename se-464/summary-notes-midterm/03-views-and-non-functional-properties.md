### Topological Goals

- **Minimize coupling** - minimize dependencies in between software components; components works independently

- **Maximize cohesion** - a component should be responsible for only one logical service

### Abstraction

- **Control abstraction** - structured programming

- **Data abstraction** - abstraction data types

- **Decomposition** - top down abstraction
    - Break problem into independent components
    
### Conway's Law

- The structure of a software system reflects the structure of the organization that built it

### Architectural representations

- **Ambiguity** - open to more than one interpretation
- **Accuracy** - correct within tolerances
- **Precision** - consistent but not necessarily correct

### View Model

- **Architecture Model** - an artifact document some or all of the architectural design decisions about a system
- **Architecture Visualization** - a way of depicting some or all of the architectural design dcisions about a system to a stakehbolder
- **Achitecture view** - a subset of related architectural design decisions

### Component Diagram

- Captures components and relationships
- APIs explicitly recorded
- Static

### Sequence Diagram

- Focus on inter-component collaboration
- Capture behaviour for specific runtime scenarios

### Deployment Diagram

- Provide mapping between components and physical devices
    - e.g. server

### Statechart Diagram

- More formal description of a system behaviour
- Poor mapping between states and components

![](/assets/Screenshot from 2018-10-22 09-01-13.png)

### FP vs. NFP

#### non-functional property

- A constraint on the manner in which the system implements and delivers its functionality
    - efficiency
    - complexity
        - proportional to the size of a system
    - scalability
        - Ability to meet new size / requirements
    - heterogeneity
        - A system's ability to be composed of, execute within, disparate parts
    - portability
        - Ability to execute on multiple platforms
    - evolvability
        - Ability to statisfy new requirements and environments
    - dependability
        - Reliability - minimize failure
        - availability - available at any given instance of time
        - robustness - ability to respond to unanticipated runtime conditions
    - fault-tolerance - ability of a system to respond gracefully to failures
    - survivability - ability to resist, recover, and adapt to threats
    - safety - the ability to avoid failures that will cause loss of life, l injury, and loss property
    
- Stakeholder may have different opinions on NFP