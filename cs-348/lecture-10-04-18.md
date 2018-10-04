## Static embedded SQL

- When the SQL is compiled, the database gives you a handle, which can be used to retrieve data via a execute command


## Embedded SQL

- SQL Statement embedded into a *host language* (C++, Fortran etc.)

|Advantages|Disadvantages|
|---|---|
|- Data preprocessing| - need preprocessor |
|- Easy to use | - Bounded to a database|

### Declarations
`EXEC SQL INCLUDE SQLCA;`
- In C, anything after the keyword `EXEC SQL` and before `;` is considered SQL code

- Can also be enclosed with an begin/end declaration

```c
EXEC SQL BEGIN DECLARE SECTION;
// C code
// Declarations of variables for SQL statements

    char db[8] = "DBCLASS";

EXEC SQL END DECLARE SECTION;

// Use the variable
EXEC SQL CONNECT TO :db;
```

- Now SQL command can refer to the `db` host variable

- Variables are proceeded with `:`

### Exception Handling

`EXEC SQL WHENEVER NOT FOUND GO TO lbl;`

- Branches to a goto label (assumes the language has goto)

### Cursors

- Used to return multiple answers
```
EXEC SQL DECLARE <name> CURSOR
    FOR SELECT <query>;
```
- Check slide 21 for a complete example

