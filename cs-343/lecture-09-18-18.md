### Syntactic Convenience

Operators:

$$=, \leq, \geq, >, <$$


$$x=y$$

x op y

- Can be both variables and constants

$$\{(snum)|\exists x_1, x_2 . STUDENT(snum, x_1, x_2)\}\equiv
\{(snum)|\exists x_1, x_2 . STUDENT(snum, -, -)\}$$

### Sample Queries (From Slide)

##### Bibliography Database
- List titles of publications written by a single author

$$\{(t) | \exists pid(PUBLICATION(pid, t)\wedge
\neg\exists a_1.(WROTE(pid, a1))\wedge\neg(a1=a)\}$$

### Integrity Constraints
- yes/no conditions that must be true in every valid database instance

#### Ex. Every Boss is an Employee
- Check slide for initial query. They are equivalent to

$$\equiv\forall x, y, z(\neg EMP(x, y, z)\vee EMP(z, -, -))$$
$$\equiv \neg \exists x, y, z\neg(\neg EMP(x, y, z)\vee EMP(z, -, -))$$
$$\equiv \neg exists x (EMP(x, -, -)\wedge \neg EMP(z, -, -))$$

### Disjoint Relationships
- e.g. Books and journals

$$\neg \exists x.(BOOK(x, -, -)\wedge JOURNAL(x, -, -, -))$$
$$\forall x.(PUB(x, -)\rightarrow(BOOK(x, -, -)\vee ...))$$

### Views
- Answers to queries can be used to define derived relations
- Tables in SQL is a view


### Domain Independence
- A query is domain independent if it evaluates to the same value in any pairs of two database instances (See slide for formal definition)

- A query that is domain independent is safe
