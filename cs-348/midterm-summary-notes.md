## Introduction
#### Three Level Schema Architecture
1. External Schema (view)
    - What the application programs and user see. May differ for different users of the same database

2. Conceptual schema
    - Description of all the logical structure of all data in the database
    
3. Physical schema
    - Description of physical aspects (files, devices, storage algorithms etc.

#### Data Independence

- **Physical** - application immune to changes in storage structures
- **Logical** - modularity; different tables are only accessed by a specialized application

#### Transactions
 - An application-specified atomic and durable unit of work
 
 - Properties of transactions ensured by the DBMS
     - **Atomic** - transaction occurs entirely, or not at all (non-divisible)
     - **Consistency** - each transaction preservers the consistency of the db
     - **Isolated** - concurrent transactions do not interfere with each other
     - **Durable** - once completed, a transaction's changes are permanent
     
#### Interfacing to the DBMS

- **Data Definition Language (DDL)**
    - Specifying schemas
    - May have different DDLs for different levels
    
- **Data Manipulation Language (DML)**
    - Specifying retrieval and revision requests
        - Navigational (procedural)
        - Non-navigational (declarative)

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
    

## SQL

#### Three parts of the language

- **DML (Data Manipulation Language)**
    - Query language
    - Update language
    
    
- **DDL (Data Definition Language)**
    - Defines schema for relations
    - Creates/modifies/destroys database objects
    
    
- **DCL (Data Control Language)**
    - Access control
    
- **Corelations** - tuple variables

- **Atomic conditions** - =, !=, <, > etc.

- **Boolean connectives** - AND, OR, NOT - combines atomic conditions


#### Set Operations

- **Relations** - answers to _SELECT_ blocks (sets of tuples)
    - _Set operations_ can be applied
    
    
- Set union: `UNION`
- Set difference: `EXCEPT`
- Set intersection: `INTERSECT`

#### HAVING clause

- The same as WHERE but for aggregate functions

#### SELECT DISTINCT caluse

- SQL is a multiset rather than a set
- Use `SELECT DISTINCT` clause to eliminate duplicates

- Add `ALL` to set operators to make them bag (multiset) operators
    - e.g. `UNION ALL`
    
#### JOIN

- `JOIN` - Inner Join; returns intersection of the two tables that satisfies the `ON` condition

- `LEFT JOIN` - returns the rows of the table on the left, and the matching rows on the right table. Returns NULL if no match

- `RIGHT JOIN` - same idea as LEFT

- `OUTER JOIN` - returns all the rows from both sides, NULL if unmatched. Combination of left and right

## Embedded SQL

##### Advantages
- Preprocessing of static parts
- Easier to use

##### Disadvantages
- Needs precompiler
- Needs to be _bound_ to a database

```c
    EXEC SQL INCLUDE SQLCA;
    main() {
        EXEC SQL BEGIN DECLARE SECTION;
            char db[6] = "cs348"
            int myVar1, myVar2;
        EXEC SQL END DECLARE SECTION;
        // Error handling
        EXEC SQL WHENEVER SQLERROR GO TO error;        
        // Connect
        EXEC SQL CONNECT TO :db;
        
        // Some operation
        
        EXEC COMMIT;
        EXEC SQL CONNECT reset;
        exit(0);
        
        // Error handling code
    error:
        EXEC SQL WHENEVER SQL ERROR CONTINUE;
        EXEC SQL ROLLBACK;
        EXEC SQL CONNECT reset;
    }
```

- If host variable is null in a SQL query the query will result in a runtime error

#### CURSOR

- Acts like an iterator, followed by a SELECT statement;
- Can be used to iterate through all the rows returned by the SELECT statement

```c
EXEC SQL DECLARE names CURSOR FOR
    SELECT name FROM author WHERE aid = :aid;
    
EXEC SQL open names;
// break when all the items are fetched
EXEC SQL WHENEVER NOT FOUND GO TO end;
for (;;) {
    EXEC SQL FETCH names INTO :name;
    cout << name << endl;
}
end: 
```

## Dynamic SQL

- Execute a string as a SQL statement

`EXEC SQL EXECUTE IMMEDIATE :string;`

- Executes the query in :string
- Does not return an answer nor contain parameters
- Used for constant statements executed only once

`EXEC SQL PREPARE stmt FROM :string;`

- :string may return answers and may contain parameters
- Can be used for repeatedly executed statements

- Can use the parameter marker `?` in the string to denote a parameter, combined with USING keyword chained by the variables

`EXEC SQL OPEN cname USING :var, :var2, :var2`

#### SQLDA

- A SQL description area that defines how a single tuple looks like, where are the data etc.
- How the DBMS communicates with the application

- A prepared statement can be _described_; the description is stored in the SQLDA structure

`EXEC SQL DESCRIBE stmt INTO sqlda`

- Can also be used to supply parameters and get the result

`EXEC SQL EXECUTE stmt USING DESCRIPTOR :sqlda;`
`EXEC SQL FETCH cname USING DESCRIPTOR :sqlda;`

###### Declaration
`struct sqlda * select;`

###### Initialization
```c
    // Initialize with number of items
    init_da(&select, i);
    // Get size
    i = select->sqld;
```

###### Access items

```c
select->sqlvar[i].sqlname.length
select->sqlvar[i].sqlname.data
select->sqlvar[i].sqltype
```

## SQL ODBC

- An interface built on library calls
    - Applications developed without access to the DB
    - Harder to use and doesn't allow preprocessing
    
- Three fundamental objects in an ODBC program
    - Environments
    - Connections
    - Statements
    
    
- CLI/ODBC can do everything Embedded SQL can
- All statements are dynamic
    - no precompilation
    - explicit binding of parameters
    
    
## E-R Modelling

- Used for database (conceptual schema) design

- Described as
    - Entities
    - Attributes
    - Relationships
    
- **Entity** - A distinguishable object

- **Entity set** - set of entities of the same type
    - Student, flight
    

- **Attributes** - describe properties of entities
    - StudentNum, StudentName, Major
    

- **Relationship** - representation of the fact that certain entities are related to each other

- **Relationship set* - set of relationships of a given type
    - Student registered in a course
    - Passengers booked on flights
    
- **Role** - the function of an entity in a relationship team

- **Role name** - an explicit indication of a role

![](/assets/Screenshot from 2018-11-01 21-52-06.png)

- Entities: Team, Location
- Attributes: TeamName, Score, Address, LocName
- Relations: Match
- Roles: HomeTeam, Visitor

- **Primary keys** - selection of attributes chosen by designer values of which determines the particular entity

#### Relationship types

- **many-to-many** (N:N) - an entity in one set can be related to many entities in the other

- **many-to-one**  (N:1) - each entity in one set can be related at most one entity in the other, but an entity in the second may be related to many entities in the first

- **one-to-many** (1:N)

- **one-to-one** (1:1) - each entity in one set can be related at most one entity in the other, and vise versa

#### Existence Dependency

- **existence dependency** - when the existence of an entity depends on the existence of another entity
    - If x is ED on y, then y is a **dominant entity** and x is a **subordinate entity**
    
    
- **Weak entity set** - an entity set containing subordinate entities
- **Strong entity set** - an entity set containing no subordinate entities

- A _weak entity set_ must have a many-to-one relationship to a distinct entity set

- **Discriminator** of a weak entity set - set of attributes that distinguish subordinate entities of the set, for a particular dominant entity
    - Primary key for a weak entity set: discriminator + primary key of entity set for dominating entities
    
#### General Cardinality Constraints

- General cardinality constraints determine lower and upper bounds on the number of relationships of a given relationship set in which a component entity may participate
    - e.g. a student may take at least 3 courses and at most 5; a course may contain at least 6 students and at most 100
    
#### Structured Attributes

- **Composite attributes** - composed of fixed number of other attributes
    - Address can contain: Street, City, Province, PostalCode


- **Multi-valued attributes** - attributes that are set valued
    - An Employee may contain many Hobbies
    
#### Aggregation

- Relationships can be viewed as higher-level entities

- e.g. Student and Course with a EnrolledIn relationship can be viewed as an entity "Enrollment"

#### Specialization

- A specialized kind of entity set may be derived from a given entity set

- Graduate students are students who have a supervisor and a number of degrees

#### Generalization

- Several entity sets can be abstracted by a more general entity set

- Car and Truck can be categorized as Vehicle

#### Disjointness

- Specialized entity sets are usually disjoint but can be declared to have entities in common

- By default specialized entities are disjoint
    - A vehicle can't be both a car and a truck

- We can declare them to overlap (e.g. utility vehicles)