## The Relational Model

- All information is organized in (a finite number of) relations
    - Simple and clean data model
    - Powerful and declarative query/update languages
    - Semantic integrity constraints
    - Data independence

- **Universe** - a set of values $$D$$ with equality (=)
- **Relation** - predicate name R, and arity $$k$$ of R (the number of columns)
    - $$R\subseteq D^k$$
- **Database** - finite set $$\rho$$ of predicate names

`AUTHOR(aid, name)`

- AUTHOR is the predicate (table headers)
- aid, name are the identifiers, also called _attributes_

- Relationships between objects (tuples) that are present in an instance are true, relationships absent are false


##### Symbols

- **Logical connectives**
    - Conjunction (and) $$\wedge$$
    - Disjunction (or) $$\vee$$
    - Negation (not) $$\neg$$
    
- **Qualifiers**
    - Existential $$\exists x$$
    

- **Valuation** a function $$\theta$$ that maps variable names to values in the universe
    - Answers to queries $$\Leftrightarrow$$ valuations to free variables that make the formula true with respect to a database
    
    
- **Query (relational calculus)** - a set comprehension of the form $$\{(x_1, ...,x_k | \phi\}$$

- **Integrity constraints** - yes/no conditions that must be true in every valid database instance
    - e.g. Every Boss is an Employee
    
- A relational _signature_ captures only the structure of relations

- _Valid database instances_ satisfy additional integrity constraints

- **Relational Database Schema** - a signature $$\rho$$ and a finite set of integrity constraints $$\Sigma$$ over $$\rho$$
    - A relational database instance **DB** conforms to a schema $$\Sigma$$
    
    
- Satisfiability of first-order formulas is undecidable

- **Domain-independent Query** - a query that produces the same result for any pairs of databases)
    - Contains only values that exist in $$R_1,...,R_k$$
    - Domain_independent + finite database => "safe"
    
    
- **Range-restricted Query** - query with a finite range

- Every domain-independent query can be written equivalently as a range restricted query

- Relational calculus is **not** Turing complete
    - There must be computable queries that cannot be written in RC
        - Built-in operations (ordering arithmetic, string etc.)
        - Counting/Aggregation
        - Reachability/Connectivity

- **Data complexity** in the size of the database, for a fixed query
    - PTIME
    - LOGSPACE
    - $$AC_0$$ (CPUs in parallel)
    

- **Combined complexity**
    - in PSPACE
    - Can express NP-hard problems (encode SAT)
    