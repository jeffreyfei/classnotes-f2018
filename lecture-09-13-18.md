## Topological Goals

- **Minimize coupling** between components. The less components know about each other, the better

- **Maximize cohesion** - components should be responsible for a single logical service within its own scope

## Abstraction

- Focus on the key issues while eliding extraneous detail
    - **Control abstraction** - structured programming
    - **Data abstraction** - abstract data types
    
## Decomposition

- Top-down abstraction is also called decomposition
    - breaking problems into independent components and describe them
    
**Conway's Law** - the *structure* of a software system reflects the structure of the *organization* that built it

## Architectural Representation

- **Ambiguity** - Multiple ways of interpretation
- **Accuracy** - Correct with tolerances
- **Precision** - Consistent but not necessarily correct

- Facilitating technical communication between stakeholders
- An opaque architecture has no value


- **Architecture Model** - an artifact documenting some or all of the architectural design decisions about a system
- **Architecture Visualization** - a way of depicting some or all of the architectural design decisions about a aystem to a stakeholder
- **Architecture View** - a subset of related architectural design decisions


- **Deployment Diagram** - provide mapping between components and physical devices
    - e.g. Servers and the services that runs on the servers
    
- **Statechart Diagram** - more formal description of system behaviour. Poor mapping between states and components

## Non-functional properties

- Constraints on how we can design our architecture
    - On the manner in which the system implements and delivers its functionality

- e.g. Quality of service, uptimes etc.

**Functional Properties** - What ithe system is supposed to do
**Non-Functional Properties** - What the system is supposed to be

- NFP can be hard to quantify

**Efficiency** - a quality that reflects a system's ability to meet its performance requirements

**Complexity** - A property that is proportional to the size of a system, its volume of constituent elements, their internal structure, and their interdependecies

**Scalability** - the ability to adapt new size / scope requirements

**Heterogeneity** - a system's ability to be composed or execute within, disparate parts

**Portability** - the ability of a system to execute on multiple platforms (while retaining their FP and NFP)

**Evolvability** - the ability to change to satisfy new requirements and environments

### Dependability

**Reliability** - the probability a system will perform within its design limits without failure over time

**Availability** - uptime

**Robustness** - the ability of a system to respond to unanticipated conditions