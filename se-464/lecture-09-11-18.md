### Factors to consider when designing
- Fitness for purpose
    - How well does the option meet our needs
- Cost of Production
    - Parts
    - Labour
    - Capital
- Cost of Operation
- Fitness for Future

### Steps of the Design Process

1. Ideation
2. Analysis
    1. Determine criteria
    2. Apply criteria
3. Selection
4. Elaboration/Refinement
5. Iteration


### Normal vs. Radical

- Existing Components = Normal
- New (invented) components = Radical
- Standard configurations = Radical
- New configurations = Normal

- *The goal is to take radical problems and turn them into normal components*


### What is Software Architecture

Components of Architecture:
- Structure
- Communication
- Nonfunctional requirements

### Functional vs. Non-Functional Requirements

**Functional** - Specific behaviour of the system

**Non-functional** - Define how a system is supposed to be
- Quality of service

### Stakeholders in a System's Architecture

- Users
- Developers
- Employer

### What is "Principal"

- Implies a degree of importance that grants a design decision
- Principal can be different for developers and users

### Prescriptive vs. Descriptive Architecture

**Prescriptive** - The design decisions made prior to the system's construction
- As-conceived or as-intended architecture

**Descriptive** - Describes how the system has been built
- As-implemented, as-realized architecture
- Hopefully adheres to the prescriptive design

### Architecture Degradation

**Architectural drift** - the introduction of principal design decisions into a system's descriptive architecture
- Still adheres to prescriptive architecture

**Architectural erosion** - the introduction of architectural design decision into a system's descriptive architecture that violate its prescriptive architecture


### Architectural Recovery

- The process of determining a software system's architecture from its implementation-level artifacts
    - Usually when architectural degradation happens
    - Can be obtained through source code, executable files, Java .class files
    
### Components

- Elements that encapsulate processing and data in a system's architecture are referred to as software components

    - Encapsulates a subset of the system's functionality and/or data
    - Restricts access that subset via an explicitly defined interface
    - Has explicitly defined dependencies on its required execution context
    
- Components typically provide application-specific services

### Connectors

- An architectural building block tasked with effecting and regulating interactions among components
    - Typically provide application-independent interaction facilities

### Configurations

- Also called topology
- A set of specific associations between the components and connectors of a software system's architecture

### Difficulty in Design

#### Complexity

**How to attack complexity**
- high-level languages
- development tools & environments
- Component-based reuse
- Development strategies (e.g. Agile)
- Emphasis on design