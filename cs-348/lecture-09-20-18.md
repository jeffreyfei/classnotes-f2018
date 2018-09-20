## Some assignment question

$$COURSE(``cs", 348, cname)\equiv COURSE(dc, cn, cname)\wedge dc=``cs"\wedge cn=348$$

## Range Restricted Queries
- See the slides for formal definition

- Range restricted => domain independent

## Computational Properties of Relational Calculus

- Evaluation of every query terminates
    - Relational calculus is not Turing complete
    
    
- *Data Complexity* in the size of the database, for a fixed query
    - The size of the number of the tuples in the database (not query)
    - in PTIME
    - in LOGSPACE
    - $$AC_0$$ (constant time on polynomially many CPUs in parallel)
    
    
- *Combined complexity*
    - In PSPACE
    - Can express NP-hard problems
    
## Query Evaluation vs. Theorem Proving

**Evaluation** - Given a query and a finite database instance find all instances to the query

**Satisfiability** - Given a query determine whether there is a (finite) database instance for which the answer is non-empty
    - Much harder (undecidable) problem
    
# SQL
- Structured Query Language
- Based on *Relational Calculus*
    - Conjunctive queries
    - Set operations
    - Update language
    - Non first-order features
    
    
- BAG (multiset) semantics
    - Possible to produce results of identical tuples
    
    
- NULL values
    - Avoid if at all possible
    
#### Three Major Parts
1. DML (Data Manipulation Language)
    - Query language
    - Update language
    
    
2. DDL (Data Definition Language)
    - Define schema for relation
    - Creates (modifies/destroys) database objects
    

3. DCL (Data Control Language)
    - Access control
    
Ex.
- Translate SQL Query back to Relational Calculus

$$\{(r1.publication) | \exists r1.author, r2.publication, r2.author, (WROTE(r1.author, r1.publication)\wedge $$
$$WROTE(r2.author, r2.publication)\wedge (r1.author\neq r2.author)\}$$

- A abbreviated version of this query is present on the slides
