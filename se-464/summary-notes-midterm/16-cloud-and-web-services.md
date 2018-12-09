# Cloud and 

### Precursor
##### Grid Computing
- Combination of computing resources from multiple administrative domains
- Used to create super computers


##### Utility Computing
- Combining computation, storage, and service metered like utilities

### NIST Essential Characteristics

- **On-demand self-service** - consumers can provision computing capabilities without human interaction

- **Broad network access** - available over the network through standard mechanisms

- **Resource pooling** - computing resource are pooled to serve multiple consumers; location independence

- **Rapid elasticity** - resource can be easily added and removed

- **Measured service** - metering of storage, processing, bandwidth etc.

##### Benefits

- Agility
- Scalability
- Cost
- Reliability
- Security


- Requires **virtualization** technology to decouple physical and computing resources


### Cloud Layers

##### Software (SaaS)

- Vendor controlled remote applications
- Concerns: control, performance, security, privacy

- e.g. Google Docs


##### Platform (PaaS)

- Vendor-controlled environment

- Limited technology choices

- e.g. AppEngine


##### Infrastructure (IaaS)

- Vendor provided resource
- Consumer provisions VM

- Concerns: More expertise needed to leverage flexibility

- e.g. AWS

### Serverless Computing

- A cloud-computing execution model in which the cloud provider acts as the server
- Dynamically managing the allocation of machine resources

### Function as a Service (FaaS)

- Provides a platform allowing customers to develop, run, and manage application functionalities without the complexity of building and maintaining the infrastructure

### Cloud Security NFPs

- User wants
    - Confidentiality
    - Integrity (of data)
    - Authenticity (data provenance)
    - Anonymity
    - Privacy
    

### Representation state transfer (REST)

- Server do not maintain session state
- Clients must not depend on direct server access

- GET, POST, PUT, DELETE


- POST vs. PUT
    - PUT -> replace resources
    - POST -> append to resources