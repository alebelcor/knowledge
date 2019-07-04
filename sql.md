# SQL

## `SELECT` statement

Used to retrieve records from a database.

### Syntax

```sql
SELECT column1, column2, ...
  FROM table_name;
```

```sql
SELECT *
  FROM table_name;
```

### Examples

Retrieve all records, showing `column1` and `column2`, from the `table_name` table:

```sql
SELECT column1, column2
  FROM table_name;
```

Retrieve all records, showing all columns, from the `table_name` table:

```sql
SELECT *
  FROM table_name;
```

## `SELECT DISTINCT` statement

Used to return unique values.

### Syntax

```sql
SELECT DISTINCT column1, column2, ...
           FROM table_name;
```

### Examples

Retrieve all (unique) records, showing `column1` and `column2`, from the `table_name` table:

```sql
SELECT DISTINCT column1, column2
           FROM table_name;
```

Retrieve the total number of unique `column1` values, from the `table_name` table:

```sql
SELECT COUNT(DISTINCT column1)
        FROM table_name;
```

## `WHERE` clause

Used to filter records via a specified condition.

Operators in the `WHERE` clause:

| Operator | Description |
|:--------:|:-----------:|
| `=` | Equal |
| `<>` or `!=` | Not equal |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal |
| `<=` | Less than or equal |
| `BETWEEN` | Between a certain range |
| `LIKE` | Search for a pattern |
| `IN` | To specify multiple possible values for a column |

### Syntax

```sql
SELECT column1, column2, ...
  FROM table_name
 WHERE condition;
```

Note: Also used in `UPDATE` and `DELETE` statements.

### Examples

Retrieve records (showing all columns), from the `table_name`, table where `column1` is `foo`:

```sql
SELECT *
  FROM table_name
 WHERE column1 = 'foo';
```

Retrieve records (showing all columns), from the `table_name`, table where `column1` is `1`:

```sql
SELECT *
  FROM table_name
 WHERE column1 = 1;
```

## `AND`, `OR` and `NOT` operators

Used in combination with `WHERE` to further filter records.

### Syntax

`AND`

```sql
SELECT column1, column2, ...
  FROM table_name
 WHERE condition1
   AND condition2
   AND condition3 ...;
```

`OR`

```sql
SELECT column1, column2, ...
  FROM table_name
 WHERE condition1
    OR condition2
    OR condition3 ...;
```

`NOT`

```sql
    SELECT column1, column2, ...
      FROM table_name
 WHERE NOT condition;
```

### Examples

Retrieve records (showing all columns), from the `table_name` table, where `column1` is `foo` and column2 is `bar`:

```sql
SELECT *
  FROM table_name
 WHERE column1 = 'foo'
   AND column2 = 'bar';
```

Retrieve records (showing all columns), from the `table_name` table, where `column1` is `foo` or `bar`:

```sql
SELECT *
  FROM table_name
 WHERE column1 = 'foo'
    OR column1 = 'bar';
```

Retrieve records (showing all columns), from the `table_name` table, where `column1` is not `foo`:

```sql
    SELECT *
      FROM table_name
 WHERE NOT column1 = 'foo';
```

## `ORDER BY` keyword

Used to sort the result set in ascending or descending order.

### Syntax

```sql
  SELECT column1, column2, ...
    FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

### Examples

Retrieve all records (showing all columns), from the `table_name` table, sorted ascending by the `column1` column:

```sql
  SELECT *
    FROM table_name
ORDER BY column1 ASC;
```

Retrieve all records (showing all columns), from the `table_name` table, sorted descending by the `column1` column:

```sql
  SELECT *
    FROM table_name
ORDER BY column1 DESC;
```

Retrieve all records (showing all columns), from the `table_name` table, sorted by the `column1` column, if some records have the same `column1` value then sort by `column2`:

```sql
  SELECT *
    FROM table_name
ORDER BY column1, column2;
```

## `INSERT INTO` statement

### Syntax

```sql
INSERT INTO table_name
            (column1, column2, column3, ...)
     VALUES (value1, value2, value3, ...);
```

When inserting values for all columns specifiying the column names is unnecessary:

```sql
INSERT INTO table_name
     VALUES (value1, value2, value3, ...);
```

### Examples

Insert a new record with values as follows: `column1=foo, column2=bar, column3=foobar`:

```sql
INSERT INTO table_name
            (column1, column2, column3)
     VALUES ('foo', 'bar', 'foobar');
```

## `NULL` Values

The representation of the absence of a value. Different than `0`, empty string or `  `.

### Syntax

`IS NULL`

```sql
SELECT column1
  FROM table_name
 WHERE column1 IS NULL;
```

`IS NOT NULL`

```sql
SELECT column1
  FROM table_name
 WHERE column1 IS NOT NULL;
```

### Examples

Retrieve records (showing column `column1`), from the `table_name` table, where `column1` value is `NULL`:

```sql
SELECT column1
  FROM table_name
 WHERE column1 IS NULL;
```

Retrieve records (showing column `column1`), from the `table_name` table, where `column1` value is not `NULL`:

```sql
SELECT column1
  FROM table_name
 WHERE column1 IS NOT NULL;
```

## `UPDATE` statement

Used to modify existing records in a table.

### Syntax

```sql
UPDATE table_name
   SET column1 = value1,
       column2 = value2,
       ...
 WHERE condition;
```

Note: Remember to include a `WHERE` clause.

### Examples

Update `column2` field with `foo` and `column3` field with `bar`, for the record that has a value of `1` on `column1` field, on the `table_name` table:

```sql
UPDATE table_name
   SET column2 = 'foo',
       column3 = 'bar'
 WHERE column1 = 1;
```

Update `column1` field with `foo`, for all records, on the `table_name` table:

```sql
UPDATE table_name
   SET column1 = 'foo';
```

## `DELETE` statement

Used to delete records in a table.

### Syntax

```sql
DELETE FROM table_name
      WHERE condition;
```

Note: Remember to include a `WHERE` clause.

## Examples

Delete the records, on table `table_name`, that have the value `foo` on the `column1` field:

```sql
DELETE FROM table_name
      WHERE column1 = 'foo';
```

Delete all records on the table `table_name`:

```sql
DELETE FROM table_name;
```
