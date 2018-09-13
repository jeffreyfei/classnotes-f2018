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
    - **Components:** 
        - Efficient components
        - Efficient communications between components
        - Keep them small
        - Simple and compact interfaces
        - Allows multiple interfaces to the same functionality
        - Separate data from processing components
        - Separate data from meta data
    
    - **Connectors:**
        - Local procedure code
        - Be careful of broadcast connectors (too much noise on each component)
        - Encourage asynchronous interaction
        - Be wary of location/distribution transparency
        
    - **Topology:**
        - Keep frequent collaborators "close"
        - Consider efficiency impact of selected styles

**Complexity** - A property that is proportional to the size of a system, its volume of constituent elements, their internal structure, and their interdependecies
    - **Components:**
        - Isolate iteraction from functioanlity
        - Restrict interactions provided by each components
    - **Connectors:**
        - Uniform and well documented protocols
    - **Topology:**
        - Low coupling

**Scalability** - the ability to adapt new size / scope requirements
    - **Components:**
        - Stateless components
        - Separate data from processing logic
        - Keep components focused
        - Simplify interfaces
        - Avoid unnecessary heterogeneity
        - Distribute data sources
        - Replicate data
    - **Connectors:**
        - Avoid bottlenecks
        - Place data close to the consumer
        - Location transparency
    - **Topology:**

**Heterogeneity** - a system's ability to be composed or execute within, disparate parts

**Portability** - the ability of a system to execute on multiple platforms (while retaining their FP and NFP)

**Evolvability** - the ability to change to satisfy new requirements and environments
    - **Components:**
        - Same as for complexity
        - Reduce risks by isolating modifications
    - **Connectors:**
        - Clearly defined responsibilities
        - Make connectors flexible
    - **Topology:**
        - Avoid implicit connectors
        - Location transparency

### Dependability

**Reliability** - the probability a system will perform within its design limits without failure over time

**Availability** - uptime

**Robustness** - the ability of a system to respond to unanticipated conditions

- **Components:**
    - Control external component depedencies
    - Support reflection (state awareness)
    - Support exception handling
- **Connectors:**
    - Use explicit connectors
    - Provide interaction guarantees
- **Topology:**
    - Avoid single points of failure
    - Enable backups
    - Support systme health monitoring
    - Support dynamic adaptation