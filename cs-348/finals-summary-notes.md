# Finals Summary Notes

- **Clustering index** - tuples in the relation with similar values for A are stored together in the same block
- **Non-clustering** - Other indices that are not clustering indices (also called secondary indices)

### Optimization

- Equivalences
- Operator implementation

- Not computationally possible to find an optimal plan

##### Simple Cost Model for disk I/O

**Uniformity**: All possible values of an attribute are equally likely to appear in a relation

**Independence** - the likelihood that an attribute has a particular value does not depend on values of other attributes

### Join Order

- Try to order intermediate results
- Nested loop join's cost is not symmetric

### Pipelined Plans

- All operators (except sorting) operator without storing intermediate results
    - No recomputation for left-deep plans
    
### Temporary Store

- General pipelined plans lead to recomputation

- Introduce store operator
    - Store intermediate result in a relation
    - Build a hash index

### Hardware Parallelism

- Multiple mass storage units
- Relational operators amenable to parallel execution