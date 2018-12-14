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