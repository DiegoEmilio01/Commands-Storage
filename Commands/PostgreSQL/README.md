# [PostgreSQL](https://www.postgresql.org/)

Click to go to an [installation guide](https://www.postgresql.org/download/) for many operating systems. From now on `PSQL` will be used to reference PostgreSQL. This guide is base on the version 12.2 of this software.

## Administration commands

| Command                     | Description                                                 |
| -------------               | :-------------                                              |
| `sudo su - postgres`        | Start PSQL server.                                          |
| `sudo -u name psql db`      | Enter directly to `db` PSQL database loggued as `name`.     |
| `psql`                      | Enter to PSQL when running the PSQL server.                 |
| `create user name with password 'pass';` | Create `name` PSQL user with `pass` password.  |
| `alter user name with superuser;`  | Give `name` superuser credentials.                   |
| `createdb db` | Create `db` database                                         |
| `psql db`     | Set `db` as being used.                                      |
| `\l`          | Print all database names (run in PSQL).                        |
| `\d`          | Print all table names.                      |
| `\du`         | Print all user names..                    |
| `\df`         | Print all stored procedure names.  |
| `\COPY entity(attr_1, attr_2) from 'entity.csv' DELIMITER ',' CSV HEADER`  | Having the table already created, insert the `.csv` data. The attributes needs to be in the `.csv` order. |
| `\c db name`  | Set `db` as being used and log in as `name`.


## Table modifications

Let `table` be the name of a table in the database in use.

| Command                       | Description                       |
| -------------                 | :-------------                    |
| `CREATE TABLE table (attr_1 type PRIMARY KEY, ..., attr_n type, FOREIGN KEY (attr_i) REFERENCES table_2(attr));` | Create a table where `type` is a PSQL [datatype](https://www.postgresql.org/docs/9.5/datatype.html) (it depends on the version).  |
| `INSERT INTO table VALUES(0, 'string', 'YYYY-MM-DD', ..., attr_n);` | Insert a tuple in the table. `INSERT` and `DELETE` can be nested querys.  |
| `ALTER TABLE table DROP COLUMN attr;` | Delete `attr` from all tuples in `table`. |
| `ALTER TABLE table ADD COLUMN attr type NOT NULL DEFAULT '';`  | Add a not null column with `''` as a defautl value. |
| `ALTER TABLE table ALTER COLUMN col SET NOT NULL;` | Set an attribute as not null. |
| `ALTER TABLE table ADD CONSTRAINT constraint_name FOREIGN KEY (attr1) REFERENCES table(attr2);` | Add a foreign key to a table. |
| `DELETE FROM table WHERE condition;` | Delete all tuples that satisfy the contition. |
| `DROP TABLE IF EXISTS table;` | Delete a table if exists. |
| `UPDATE table SET attribute=input WHERE condition;` | Update all tuples that satisfy the contition. |
| `ALTER TABLE table DROP CONSTRAINT table_attr_fkey;` | Delete a reference to an external table. |
| `CREATE SEQUENCE table_attr_seq START WITH max_attr + 1;` | Create a sequence. Useful to simulate a `SERIAL` datatype. |
| `ALTER SEQUENCE table_attr_seq OWNED BY table.attr;` | Assign the sequence to an attribute. |
| `ALTER TABLE table ALTER COLUMN attr SET DEFAULT nextval('table_attr_seq');`	| Set `table` `attr` to follow the sequence assigned (set `attr` to not null if is not). |


## Relacional SQL


| Command                       | Description                       |
| -------------                 |:-------------                     |
| `SELECT DISTINCT attribute_1, ..., attribute_n INTO table`	| **Projection**. `DISTINCT` for the answer to be a set. `INTO` inserts the values in another table (`IN external_db` can be used), and the values can be save in a variable. |
| `WHERE condition_1 AND cond_2 OR NOT cond_3` | **Selection**. Conditions like `=`, `>=`, `<`, `<>` (distinct), etc. can be used. |
| `attr LIKE '_input%'` | Check a match. Use `%` to make match with many characters or '\_' with just one. |
| `attr IN query` | Check if `attr` is in the result of `query`. |
| `attr operator ANY/ALL (subquery)` | Used to compare an attribute with a subquery result. `All` returns `TRUE` if the condition is `TRUE` for every tuple (non-monotonic). `ANY` is similar but `TRUE` if there is any (monotonic). |
| `attr ~* regex`         | Check a case-insensitive regex match (without `*` for case-sensitive). |
| `EXISTS (subquery)`     | `TRUE` when the subquery returns at least one tuple. |
| `\|\|`                    | String concatenation. |
| `FROM table_1, table_2` | **Cross product** of both tables (can be extended). |
| `SELECT attributes FROM table_1, table_2 WHERE condition` | **Join** of both tables. |
| `query_1 UNION query_2` | **Union**. Work with sets, there aren't duplicates. `UNION ALL` returns with duplicates. |
| `query_1 INTERSECT query_2` | **Intersection**. |
| `query AS new_name` | **Rename** a subquery. Tables, aggregations or attributes can also be renamed. |
| `query_1 EXCEPT query_2` | **Difference**. Non-monotonic operator. |

## Aggregation

| Command                 | Description                   |
| -------------           | :-------------                 |
| `COUNT(DISTINCT attr)`  | Count how many different values are.  |
| `MAX(attr)`             | Return the maximum of `attr`. |
| `MIN(attr)`             | Return the minimum of `attr`. |
| `SUM(attr)`             | Sum a numeric attribute when there is aggregation by other attribute. |
| `GROUP BY attr`         | **Aggregation** by `attr`. Include all projected attributes (frequently used with `COUNT`). |
| `HAVING condition`      | After `GROUP BY` and before `ORDER BY`. Used for selection in a aggregation (aliases can't be used). |
| `ORDER BY attr`         | **Order** by `attr`. `ASC` or `DESC` at the end of the query. |

## Iteration

`WHILE` and `LOOP` also exists. Is not mandatory to declare ato include an empty variable. In thr aftet that last of the following cases the variable must be `RECORD` type.

```sql
FOR var IN a...b LOOP	
    sql_statement
END LOOP;

FOR record_var IN sql_query LOOP
    sql_statement
END LOOP;
```

## Conditionals

```sql
IF boolean_condition THEN
    sql_statement
ELSE
    sql_statement
END IF;

CASE WHEN boolean_condition THEN sql_statement;
    ...
    WHEN boolean_condition_n THEN sql_statement_n-1;
    ELSE sql_statement_n;
END CASE;
```


## Recursion

```sql
WITH RECURSIVE recursive_table(attr_1, attr_2) AS
(
   SELECT * FROM table
   UNION
   SELECT T.attr_1, TR.attr_2 FROM table AS T, recursive_table AS TR WHERE condition
)
SELECT * FROM recursive_table;
```


## Dynamic SQL

`EXECUTE` executes a query, represented as a string, with dynamic variables (its values can change during execution).

```sql
EXECUTE 'query with $1, ..., $n;' USING attr_1, ..., attr_n;
```

## Stored procedures [PL/PgSQL](https://www.postgresql.org/docs/12/plpgsql.html)

A procedure can be stored in Stored in a file like `fn_name.sql` (without the `;` at the end of the procedure) or within the database in a special table. You can run the terminal in the folder where the file is stored to import the procedure to PSQL with `\i fn_name.sql`.

```sql
# Declaration
CREATE OR REPLACE FUNCTION fn_name (attr_1 type_1, ..., attr_n type_n)
RETURNS result_type AS
# Use void when nothing is returned. Valid types are: INTEGER, TABLE(attr_1 type_1,...), etc.
$$
DECLARE
    variable_declaration;   # Declare procedure variables and its type.
BEGIN
    sql_statement RETURN var; # Can include querys.
    # 'RETURN QUERY' to assign the query to a table declared as variable. Is mandatory to include an empty `RETURN` after that.
END
$$ LANGUAGE plpgsql;

# Ussage of the procedure
SELECT fn_name(input_1, ..., input_n);

# To import a stored procedure in a database
\i fn_name.sql

# Variable declaration
var := to_char(i, '999999999');
# The value of the previous variable is set as the result of another function.
```