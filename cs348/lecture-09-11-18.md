# Relation Model

1. Theory
2. Standards
3. Deployed technology

### Set Comprehension

$$\{(x_1,...,x_k)| (condition)\}$$

- All *k-tuples* of values that satisfy (condition)

#### How do we ask questions

##### Find all pairs of (natural) numbers that add to 5

Question: $$\{(x, y) | PLUS(x, y, 5))\}$$

Answer: $$\{(0, 5), (1, 4), (2, 3), (3, 2), (4, 1), (5, 0)\})$$

##### Find all pairs of numbers that add to the same number as they subtract to
(i.e., $$x+y=x-y$$)

Question: $$\{(x, y) | \exists z.PLUS(x, y, z)\wedge PLUS(z, y, x)\}$$

Answer: $$\{(0, 0), (1, 0), ..., (5, 5)\}$$

- Answer depends on the content (instance) of PLUS
    - In other words the content of the PLUS table
    
##### Find the neutral element (of addition)

Question: $$\{(x)|PLUS(x, x, x)\}$$
Answer: $$\{0\}$$

##### Consider the following table
![](/assets/Screenshot from 2018-09-11 08-59-56.png)

##### Find the pairs of emp-s working for the same boss

Q: $$\{(x_1, x_2) | \exists y_1, y_2, z.EMP(x_1, y_1, z)\wedge EMP(x_2, y_2, z)\}$$

A: $$\{(Sue, Bob), (Fred, John), (Jim, Eve)\}$$

- Note that repetition is possible (e.g. $$(Sue, Sue)$$
    - Needs extra condition (e.g. $$x_1 != x_2$$)
    
    
### Idea of Relational Model

- All information is organized in (a finite number of) relations

**Features:**

- Simple and clean data model
- Powerful and declarative query/update languages
- semantic integrity constraints
- Data independence

#### Components:

**Universe** 
- A set of values **D** with equality (=)

**Relation** 
- Predicate name R, and airty *k* of R (the number of columns)
- a relation $$R\subseteq D^k$$

**Database**
- Signature: finite set $$\rho$$ of pedicate names
- Instance: a relation $$R_i$$ for each $$R_i$$

Signature: $$\rho = (R_1,...,R_n)$$
Instance: $$DB=(D, =, R_1, ..., R_n)$$

#### A Bibliography Relational Database Signature

##### Predicates (also called table headers):

```
AUTHOR(aid, name)
WROTE(author, publication)
PUBLICATION(pubid, title)
```

- table identifiers in caps
- column names in the brackets

##### Relations (also called tables):
- Examples of a collection of factual data in the tables

**AUTHOR** = $$\{(1, John),(2, Sue)\}$$
**WROTE** = $$\{(1, 1), (1, 4), (2, 3)\}$$
...

#### Atomic "Turth"

- Relationships between objects that are present in an instance are true, relationships absent are false

e.g. (The sample Bibliography database instance)
- "John" is an author with id "1": $$(1, John)\in AUTHOR$$
- "Mathematical Logic" is a publication: $$(1, Mathematical~{}Logic)\in PUBLICATION$$
- "John" has NOT written "Trans. Databases": $$(1, 3)\notin WROTE$$

#### BNF Grammar
- A compact way of expressing languages


**Valuation** - a function $$\theta$$ that maps variable names to values in the universe

- The *truth* of a formula $$\phi$$ is defined with respect to

1. A database instance **$$DB=(D, =, R_1, R_2, ...)$$**
2. A valuation $$\theta: \{x_1, x_2,...\}\rightarrow D$$


**Query** - a set comprehension of the form $$\{(x_1, ..., x_k)|\phi\}$$

**Free Variables**
- A formula that has no free variables expresses is called a *sentence*