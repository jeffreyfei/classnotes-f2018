### Security

- **Confidentiality** - preventing unauthorized parties from accessing the information or perhaps even being aware of the existence of information

- **Integrity** - only authorized parties can manipulate the information in authorized ways

- **Availability** - resources are available at any given time by authorized parties

### Design Principles for Security

- **Least Privilege** - only give privileges when neccessary
- **Fail-safe Defaults** - deny access if explicit permission is absent
- **Economy of Mechanism** - adopt simple security mechanisms
- **Complete Mediation** - Ensure every access is permitted
- **Open Design** - do not reply on secrecy
- **Separation of Privilege** - introduce multiple parties to avoid exploitation of privileges
- **Least Common Mechanism** - limit critical resource sharing to only a few machanisms
- **Pyschological Acceptability** - make security mechanisms usable
- **Defense in Depth** - have multiple layers of countermeasures

### Discretionary Access Control
- Based on identity of the requestor, the resource, and whether the requestor has permission to access

### Mandatory Access Control
- Policy based

**Impersonation** - pretend to be a trusted party
**Fradulent Actions** - deception
**Misrepresentation** - false information on a party
**Collusion** - malicious actions that involves multiple parties
**Addition of Unknown** - a new party to the system which affects the functioning of the entire system due to the lack of trust

#### Ex. Chrome

- Relies on least privilege, separation of privilege, and defence in depth to securely parse and render insecure content