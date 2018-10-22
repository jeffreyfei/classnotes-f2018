### Factors
- Fitness for purpose
- Cost of production
- Cost of operation
- Fitness for future

### Design Process
1. Ideation
2. Analysis
    1. Determine criteria
    2. Apply criteria
3. Selection
4. Elaboration / refinement
5. Iteration

### Role of developer

Existing components / standard configuration => Normal
New components / configurations => Radical

- Take radical problems and turn into normal problems

### What is Software Architecture
- The set of *principal design decisions* about the system
- Blueprint for a software system's construction and evolution

- *All architecture is design but not all design is architecture*

- **Architecture** - parts of a system that would be difficult change once the system is built
    - Structure
    - Communication
    - Nonfunctional requirements
    
    
##### ANSI/IEEE 1471-200

Architecture is the **fundamental organization** of a system, embodied in its **components**, their **relationships** to each other and the environment, and the **principles** governing its design and evolution

##### Eoin Woods

Software architecture is the set of **design decisions** which, if made incorrectly, may cause your project to be cancelled

### Requirements
**Functional requirements** - defines specifics behaviour; what a system is supposed to do
**Non-functional requirements** - criteria that can be used to judge the performance of a system; how a system is supposed to be

### Principal

- A degree of importance that grants a design decision "architectural status"
- Depend on what the stakeholders define as the system goals

### Architecture

**Prescriptive architecture** - the design decisions made prior to the system's construction

**Descriptive architecture** - how the system has been built


### Evolution

- Ideally prescriptive architecture evolves first
- In practice descriptive architecture directly modified

### Architectural Degradation

- **Architectural drift** - design decisions not included in prescriptive architecture, but *do not violate* the decisions made in p.a.

- **Architectural erosion** - design decisions introduced to descriptive architecture that violates the prescriptive architecture

### Architectural Recovery

- The process of determining a software system's architecture from its implementation-level artifacts

### Software components

- Elements that encapsulate processing and data in a system's architecture
    - Encapsulates functionality / data
    - Restricts access
    - Explicitly defined dependencies
    
### Software connectors

- An architectural building block tasked with effecting a regulating interactions among components

### Architectural configurations

- Set of specific associations between the components and connectors of a software system's architecture

### Deployment

- Executable modules placed on hardware devices to run
- For a software system to fulfill its purpose

### Essential difficulties

- Complexity
    - Can be alleviated by high-level languages, dev tools, reusable components, dev strategies etc.
- Conformity
- Changeability
- Intangibility