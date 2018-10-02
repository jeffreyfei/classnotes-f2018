## What is DB2

- A command-line interface to SQL
- An ESQL preprocessor for C language

## Ordering Results
#### Side

`LIMIT k` is sql is non-deterministic

### NULL value (What does it mean?)

|Name|Office Phone|Home Phone
|---|---|---|
|Joe|1234|2323|
|Sue|2341|NULL|

##### Possibility 1
- Value inapplicable
    - Better design would be splitting into two tables (although sometimes tables are combine for performance reasons)
    
##### Possibility 2
- Value unknown

## Value Unknown and Queries

- Answers true in all possible worlds W of an incomplete D
- NP hard
- SQL use a crude approximation

- A *NULL* as a parameter to an operation (should) makes the result NULL
`1+NULL->NULL`
`"foo" || NULL -> NULL`
    - Comparison with a NULL value return UNKNOWN
    - However proper logical behaviour should still hold
        - e.g. `x=0 OR x!=0` should always be `true`

- Three-valued logic
unique special value for duplicates
- Doesn't count (value inapplicable)

### Unknown and Boolean Connectives
- Boolean operations have to handle UNKOWN
    - Extended truth tables for Boolean connectives
    - `(x=0) || (x <> 0)` where `x=UNKNOWN` is `(UNKNOWN)||(UNKNOWN)=UNKNOWN)`
    
### Unknown in WHERE clauses

- Adds `IS UNKNOWN` in addition to `IS TRUE` and `IS FALSE`

### Counting NULLS

- `COUNT(url)` only counts non-null urls
- `COUNT(*)` counts rows (include ones with NULL values)

### Outer  Join
- Allow *NULL-padded* answers that *fail to satisfy* a conjunct in a conjunction


$$\{(x, y, z)|(R(x, y) \wedge S(y, z)$$
$$\vee (z=NULL\wedge R(x, y)\wedge \neg\exists
z.(S(y,z)))$$ (LEFT or FULL)
$$\vee(x=NULL \wedge S(y, z)\wedge \neg\exists
x.(R(x, y)))$$ (RIGHT or FULL)
$$\}$$


### Overall

- `NULL`s are necessary evil
    - Used to account for small irregularities in data

- Can always be avoided
    - May produce inefficient solution
    
- Can't escape `NULL`s in practice


### DB2 Instructions
- Check slides