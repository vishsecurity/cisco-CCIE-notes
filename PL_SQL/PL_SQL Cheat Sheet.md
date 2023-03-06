# PL/SQL Cheat Sheet

![PL/SQL Cheat Sheet](https://simplecheatsheet.com/wp-content/uploads/2020/07/Colorful-Pop-Tutorial-Youtube-Thumbnail-3.png)

The **PL/SQL cheat sheet** includes symbol syntax and methods to help you using PL/SQL. **ORACLE PL/SQL** is an extension of SQL language that combines the data manipulation power of SQL with the processing power of procedural language to create super-powerful SQL queries. PL/SQL means instructing the compiler ‘what to do’ through SQL and ‘how to do’ through its procedural way.

## [PL/SQL: Data Types Cheat Sheet](https://simplecheatsheet.com/pl-sql-data-types/)

| **Scalar**             | Single values with no internal components, such as a **NUMBER, DATE,** or **BOOLEAN**. |
| ---------------------- | ------------------------------------------------------------ |
| **Large Object (LOB)** | Pointers to large objects that are stored separately from other data items, such as text, graphic images, video clips, and sound waveforms. |
| **Composite**          | Data items that have internal components that can be accessed individually. For example, collections and records. |
| **Reference**          | Pointers to other data items.                                |

##### **Scalar Data Types and Subtypes**

| **Date Type** | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| **Numeric**   | Numeric values on which arithmetic operations are performed. |
| **Character** | Alphanumeric values that represent single characters or strings of characters. |
| **Boolean**   | Logical values on which logical operations are performed.    |
| **Datetime**  | Dates and times.                                             |

##### **Numeric Data Types and Subtypes**

| **Data Type**            | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| **PLS_INTEGER**          | Signed integer in range -2,147,483,648 through 2,147,483,647, represented in 32 bits |
| **BINARY_INTEGER**       | Signed integer in range -2,147,483,648 through 2,147,483,647, represented in 32 bits |
| **BINARY_FLOAT**         | Single-precision IEEE 754-format floating-point number       |
| **BINARY_DOUBLE**        | Double-precision IEEE 754-format floating-point number       |
| **NUMBER(prec, scale)**  | Fixed-point or floating-point number with absolute value in range 1E-130 to (but not including) 1.0E126. A NUMBER variable can also represent 0 |
| **DEC(prec, scale)**     | ANSI specific fixed-point type with maximum precision of 38 decimal digits |
| **DECIMAL(prec, scale)** | IBM specific fixed-point type with maximum precision of 38 decimal digits |
| **NUMERIC(pre, secale)** | Floating type with maximum precision of 38 decimal digits    |
| **DOUBLE PRECISION**     | ANSI specific floating-point type with maximum precision of 126 binary digits (approximately 38 decimal digits) |
| **FLOAT**                | ANSI and IBM specific floating-point type with maximum precision of 126 binary digits (approximately 38 decimal digits) |
| **INT**                  | ANSI specific integer type with maximum precision of 38 decimal digits |
| **INTEGER**              | ANSI and IBM specific integer type with maximum precision of 38 decimal digits |
| **SMALLINT**             | ANSI and IBM specific integer type with maximum precision of 38 decimal digits |
| **REAL**                 | Floating-point type with maximum precision of 63 binary digits (approximately 18 decimal digits) |

Below is a valid declaration

```
DECLARE 
   num1 INTEGER; 
   num2 REAL; 
   num3 DOUBLE PRECISION; 
BEGIN 
   null; 
END; 
/ 
```

##### **Character Data Types and Subtypes**

| **Data Type** | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| **CHAR**      | A fixed-length character string with a maximum size of 32,767 bytes |
| **VARCHAR2**  | A variable-length character string with a maximum size of 32,767 bytes |
| **RAW**       | A variable-length binary or byte string with a maximum size of 32,767 bytes, not interpreted by PL/SQL |
| **NCHAR**     | A fixed-length national character string with a maximum size of 32,767 bytes |
| **NVARCHAR2** | A variable-length national character string with a maximum size of 32,767 bytes |
| **LONG**      | A variable-length character string with a maximum size of 32,760 bytes |
| **LONG RAW**  | A variable-length binary or byte string with a maximum size of 32,760 bytes, not interpreted by PL/SQL |
| **ROWID**     | Physical row identifier, the address of a row in an ordinary table |
| **UROWID**    | Universal row identifier (physical, logical, or foreign row identifier) |

##### Datetime and Interval Types

| Field Name      | Valid Datetime Values                                        | Valid Interval Values                                        |
| --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| YEAR            | -4712 to 9999 (excluding year 0)                             | Any nonzero integer                                          |
| MONTH           | 01 to 12                                                     | 0 to 11                                                      |
| DAY             | 01 to 31 (limited by the values of MONTH and YEAR, according to the rules of the calendar for the locale) | Any nonzero integer                                          |
| HOUR            | 00 to 23                                                     | 0 to 23                                                      |
| MINUTE          | 00 to 59                                                     | 0 to 59                                                      |
| SECOND          | 00 to 59.9(n), where 9(n) is the precision of time fractional seconds | 0 to 59.9(n), where 9(n) is the precision of interval fractional seconds |
| TIMEZONE_HOUR   | -12 to 14 (range accommodates daylight savings time changes) | Not applicable                                               |
| TIMEZONE_MINUTE | 00 to 59                                                     | Not applicable                                               |
| TIMEZONE_REGION | Found in the dynamic performance view V$TIMEZONE_NAMES       | Not applicable                                               |
| TIMEZONE_ABBR   | Found in the dynamic performance view V$TIMEZONE_NAMES       | Not applicable                                               |

##### PL/SQL Large Object (LOB) Data Types

| Data Type | Description                                                  | Size                                              |
| --------- | ------------------------------------------------------------ | ------------------------------------------------- |
| BFILE     | Used to store large binary objects in operating system files outside the database. | System-dependent. Cannot exceed 4 gigabytes (GB). |
| BLOB      | Used to store large binary objects in the database.          | 8 to 128 terabytes (TB)                           |
| CLOB      | Used to store large blocks of character data in the database. | 8 to 128 TB                                       |
| NCLOB     | Used to store large blocks of NCHAR data in the database.    | 8 to 128 TB                                       |

## [PL/SQL: Variables, Constants, and Literals Cheat Sheet](https://simplecheatsheet.com/pl-sql-variables-constants-and-literals/)

##### Variables

```
Variable_name  datatype(size);
```

##### Constants

```
Constant_Name  constant  Datatype(size) := value;
```

##### Literals

| **Literal Type**           | Example                                                      |
| -------------------------- | ------------------------------------------------------------ |
| **Numeric Literals**       | 050 78 -14 0 +327676.6667 0.0 -12.0 3.14159 +7800.006E5 1.0E-8 3.14159e0 -1E38 -9.5e-3 |
| **Character Literals**     | ‘A’ ‘%’ ‘9’ ‘ ‘ ‘z’ ‘(‘                                      |
| **String Literals**        | ‘Hello, world!”Tutorials Point”19-NOV-12’                    |
| **BOOLEAN Literals**       | TRUE, FALSE, and NULL.                                       |
| **Date and Time Literals** | DATE ‘1978-12-25’;TIMESTAMP ‘2012-10-29 12:01:01’;           |

## [PL/SQL: Operators Cheat Sheet](https://simplecheatsheet.com/pl-sql-operators/)

##### Arithmetic Operators

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| +        | Adds two operands                                            |
| –        | Subtracts second operand from the first                      |
| *        | Multiplies both operands                                     |
| /        | Divides numerator by de-numerator                            |
| **       | Exponentiation operator, raises one operand to the power of other |

##### Relational Operators

| **Operator** | **Description**                                              |
| ------------ | ------------------------------------------------------------ |
| =            | Checks if the values of two operands are equal or not, if yes then condition becomes true. |
| !=<>~=       | Checks if the values of two operands are equal or not, if values are not equal then condition becomes true. |
| >            | Checks if the value of left operand is greater than the value of right operand, if yes then condition becomes true. |
| <            | Checks if the value of left operand is less than the value of right operand, if yes then condition becomes true. |
| >=           | Checks if the value of left operand is greater than or equal to the value of right operand, if yes then condition becomes true. |
| <=           | Checks if the value of left operand is less than or equal to the value of right operand, if yes then condition becomes true. |

##### Comparison Operators

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| LIKE     | The LIKE operator compares a character, string, or CLOB value to a pattern and returns TRUE if the value matches the pattern and FALSE if it does not. |
| BETWEEN  | The BETWEEN operator tests whether a value lies in a specified range. x BETWEEN a AND b means that x >= a and x <= b. |
| IN       | The IN operator tests set membership. x IN (set) means that x is equal to any member of set. |
| IS NULL  | The IS NULL operator returns the BOOLEAN value TRUE if its operand is NULL or FALSE if it is not NULL. Comparisons involving NULL values always yield NULL. |

##### Logical Operators

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| and      | Called the logical AND operator. If both the operands are true then condition becomes true. |
| or       | Called the logical OR Operator. If any of the two operands is true then condition becomes true. |
| not      | Called the logical NOT Operator. Used to reverse the logical state of its operand. If a condition is true then Logical NOT operator will make it false. |

## [PL/SQL: Conditions Cheat Sheet](https://simplecheatsheet.com/pl-sql-conditions/)

##### IF-THEN Statement

```
IF condition THEN  
   Statement; 
END IF; 
```

##### IF-THEN-ELSE Statement

```
IF condition THEN 
   Statement1;  
ELSE  
   Statement2; 
END IF;
```

##### IF-THEN-ELSIF Statement

```
IF(boolean_expression 1)THEN  
   Statement1; -- Executes when the boolean expression 1 is true  
ELSIF( boolean_expression 2) THEN 
   Statement2;  -- Executes when the boolean expression 2 is true  
ELSIF( boolean_expression 3) THEN 
   Statement3; -- Executes when the boolean expression 3 is true  
ELSE  
   Statement4; -- executes when the none of the above condition is true  
END IF; 
```

##### CASE Statement

```
CASE selector 
   WHEN 'value1' THEN Statement1; 
   WHEN 'value2' THEN Statement2; 
   WHEN 'value3' THEN Statement3; 
   ... 
   ELSE Sn;  -- default case 
END CASE;
```

##### Searched CASE Statement

```
CASE 
   WHEN selector = 'value1' THEN Statement1; 
   WHEN selector = 'value2' THEN Statement2; 
   WHEN selector = 'value3' THEN Statement3; 
   ... 
   ELSE Sn;  -- default case 
END CASE; 
```

##### Nested IF-THEN-ELSE Statements

```
IF( boolean_expression 1)THEN 
   -- executes when the boolean expression 1 is true  
   IF(boolean_expression 2) THEN 
      -- executes when the boolean expression 2 is true  
      sequence-of-statements; 
   END IF; 
ELSE 
   -- executes when the boolean expression 1 is not true 
   else-statements; 
END IF; 
```

## [PL/SQL: Loops Cheat Sheet](https://simplecheatsheet.com/pl-sql-loops/)

##### Basic Loop

```
LOOP 
   Sequence of statements; 
END LOOP; 
```

##### WHILE Loop

```
WHILE condition LOOP 
   sequence_of_statements 
END LOOP; 
```

##### FOR Loop

```
FOR counter IN initial_value .. final_value LOOP 
   sequence_of_statements; 
END LOOP;
```

##### Nested Loops

- **Nested basic LOOP**

```
LOOP 
   Sequence of statements1 
   LOOP 
      Sequence of statements2 
   END LOOP; 
END LOOP;
```

- **Nested FOR LOOP** 

```
FOR counter1 IN initial_value1 .. final_value1 LOOP 
   sequence_of_statements1 
   FOR counter2 IN initial_value2 .. final_value2 LOOP 
      sequence_of_statements2 
   END LOOP; 
END LOOP;
```

- **Nested WHILE LOOP**

```
WHILE condition1 LOOP 
   sequence_of_statements1 
   WHILE condition2 LOOP 
      sequence_of_statements2 
   END LOOP; 
END LOOP; 
```

##### EXIT statement 

```
EXIT;
```

##### CONTINUE statement

```
CONTINUE;
```

##### GOTO statement 

```
GOTO label;
..
..
<< label >>
statement;
```

## [PL/SQL: Arrays Cheat Sheet](https://simplecheatsheet.com/pl-sql-arrays/)

##### Creating a Varray Type

```
CREATE OR REPLACE TYPE varray_type_name IS VARRAY(n) of <element_type>
```

Where,

- *`varray_type_name`* is a valid attribute name,
- *`n`* is the number of elements (maximum) in the varray,
- *`element_type`* is the data type of the elements of the array.

##### Resize the max size of array

```
CREATE Or REPLACE TYPE PrintArray AS VARRAY(10) OF VARCHAR2(10);
```

##### Drop the varray

```
DROP TYPE varray_type_name ;
```

## [PL/SQL: Functions Cheat Sheet](https://simplecheatsheet.com/pl-sql-functions/)

##### Creating a Function

```
CREATE [OR REPLACE] FUNCTION function_name 
[(parameter_name [IN | OUT | IN OUT] type [, ...])] 
RETURN return_datatype 
{IS | AS} 
BEGIN 
   < function_body > 
END [function_name];
```

Where,

- *`function-name`* specifies the name of the function.
- `[OR REPLACE]` the option allows the modification of an existing function.
- The optional parameter list contains the name, model, and types of the parameters. IN represents the value that will be passed from outside and OUT represents the parameter that will be used to return a value outside of the procedure.
- The function must contain a **return** statement.
- The `RETURN` clause specifies the data type you are going to return from the function.
- *`function-body`* contains the executable part.
- The `AS` keyword is used instead of the `IS` keyword for creating a standalone function.

##### Drop Function

```
DROP FUNCTION function_name;
```

## [PL/SQL: Cursors Cheat Sheet](https://simplecheatsheet.com/pl-sql-cursors/)

##### Implicit Cursors

Below is table provides the description of the most used attributes

| `%FOUND`    | Returns TRUE if an INSERT, UPDATE, or DELETE statement affected one or more rows or a SELECT INTO statement returned one or more rows. Otherwise, it returns FALSE. |
| ----------- | ------------------------------------------------------------ |
| `%NOTFOUND` | The logical opposite of %FOUND. It returns TRUE if an INSERT, UPDATE, or DELETE statement affected no rows, or a SELECT INTO statement returned no rows. Otherwise, it returns FALSE. |
| `%ISOPEN`   | Always returns FALSE for implicit cursors, because Oracle closes the SQL cursor automatically after executing its associated SQL statement. |
| `%ROWCOUNT` | Returns the number of rows affected by an INSERT, UPDATE, or DELETE statement, or returned by a SELECT INTO statement. |

Any SQL cursor attribute will be accessed as `sql%attribute_name`

##### Explicit Cursors

```
CURSOR cursor_name IS select_statement; 
```

##### Declaring the Cursor

```
CURSOR c_customers IS 
   SELECT id, name, address FROM customers; 
```

##### Opening the Cursor

```
OPEN c_customers; 
```

##### Fetching the Cursor

```
FETCH c_customers INTO c_id, c_name, c_addr; 
```

##### Closing the Cursor

```
CLOSE c_customers;
```

## [PL/SQL: Exceptions Cheat Sheet](https://simplecheatsheet.com/pl-sql-exceptions/)

##### Exception Handling

The default exception will be handled using ***WHEN others THEN\***

```
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)> 
EXCEPTION 
   <exception handling goes here > 
   WHEN exception1 THEN  
      exception1-handling-statements  
   WHEN exception2  THEN  
      exception2-handling-statements  
   WHEN exception3 THEN  
      exception3-handling-statements 
   ........ 
   WHEN others THEN 
      exception3-handling-statements 
END;
```

##### Raising Exceptions

Below is the simple syntax for raising an exception:

```
DECLARE 
   exception_name EXCEPTION; 
BEGIN 
   IF condition THEN 
      RAISE exception_name; 
   END IF; 
EXCEPTION 
   WHEN exception_name THEN 
   statement; 
END; 
```

##### User-defined Exceptions

```
DECLARE 
   my-exception EXCEPTION; 
```

## [PL/SQL: Triggers Cheat Sheet](https://simplecheatsheet.com/pl-sql-triggers/)

Below is syntax for creating a trigger:

```
CREATE [OR REPLACE ] TRIGGER trigger_name  
{BEFORE | AFTER | INSTEAD OF }  
{INSERT [OR] | UPDATE [OR] | DELETE}  
[OF col_name]  
ON table_name  
[REFERENCING OLD AS o NEW AS n]  
[FOR EACH ROW]  
WHEN (condition)   
DECLARE 
   Declaration-statements 
BEGIN  
   Executable-statements 
EXCEPTION 
   Exception-handling-statements 
END; 
```

Where,

- `CREATE [OR REPLACE] TRIGGER trigger_name` − Creates or replaces an existing trigger with the *trigger_name*.
- `{BEFORE | AFTER | INSTEAD OF}` − This specifies when the trigger will be executed. The INSTEAD OF clause is used for creating a trigger on a view.
- `{INSERT [OR] | UPDATE [OR] | DELETE}` − This specifies the DML operation.
- `[OF col_name]` − This specifies the column name that will be updated.
- `[ON table_name]` − This specifies the name of the table associated with the trigger.
- `[REFERENCING OLD AS o NEW AS n]` − This allows you to refer new and old values for various DML statements, such as INSERT, UPDATE, and DELETE.
- `[FOR EACH ROW]` − This specifies a row-level trigger, i.e., the trigger will be executed for each row being affected. Otherwise, the trigger will execute just once when the SQL statement is executed, which is called a table-level trigger.
- `WHEN (condition)` − This provides a condition for rows for which the trigger would fire. This clause is valid only for row-level triggers.

**Types of PL/SQL Triggers**

- **Row-level trigger** – An event is triggered for each row updated, inserted, or deleted.
- **Statement level trigger** – An event is triggered for each SQL statement executed.

## [PL/SQL: Packages Cheat Sheet](https://simplecheatsheet.com/pl-sql-packages/)

Below is the syntax for creating PL/SQL package specification:

```
CREATE [OR REPLACE] PACKAGE package_name [ AUTHID { CURRENT_USER | DEFINER } ] { IS | AS }
```

##### Package Body

```
CREATE [OR REPLACE] PACKAGE BODY package_name { IS | AS }
```

##### Package elements

```
package_name.package_element
```

## [PL/SQL: Collections Cheat Sheet](https://simplecheatsheet.com/pl-sql-collections/)

##### Varrays

```
TYPE <type_name> IS VARRAY (<SIZE>) OF <DATA_TYPE>;
```

the memory allocation of Varray (dense) diagrammatically.

| Subscript | 1    | 2    | 3    | 4    | 5    | 6    | 7    |
| --------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Value     | Xyz  | Dfv  | Sde  | Cxs  | Vbc  | Nhu  | Qwe  |

##### Nested Tables

```
TYPE type_name IS TABLE OF element_type [NOT NULL]; 

table_name type_name;
```

The memory allocation of Nested Table (dense and sparse) diagrammatically. The black-colored element space denotes the empty element in a collection i.e. sparse.

| Subscript     | 1    | 2    | 3    | 4    | 5    | 6    | 7    |
| ------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Value (dense) | Xyz  | Dfv  | Sde  | Cxs  | Vbc  | Nhu  | Qwe  |
| Value(sparse) | Qwe  |      | Asd  | Afg  |      | Asd  | Wer  |

##### Index-by Table

```
TYPE type_name IS TABLE OF element_type [NOT NULL] INDEX BY subscript_type; 

table_name type_name;
```

The memory allocation of Nested Table (sparse) diagrammatically. The black-colored element space denotes the empty element in a collection i.e. sparse.

| Subscript (varchar) | FIRST | SECOND | THIRD | FOURTH | FIFTH | SIXTH | SEVENTH |
| ------------------- | ----- | ------ | ----- | ------ | ----- | ----- | ------- |
| Value(sparse)       | Qwe   |        | Asd   | Afg    |       | Asd   | Wer     |

##### Collection Methods

| `EXISTS(n)`   | Returns TRUE if the nth element in a collection exists; otherwise returns FALSE. |
| ------------- | ------------------------------------------------------------ |
| `COUNT`       | Returns the number of elements that a collection currently contains. |
| `LIMIT`       | Checks the maximum size of a collection.                     |
| `FIRST`       | Returns the first (smallest) index numbers in a collection that uses the integer subscripts. |
| `LAST`        | Returns the last (largest) index numbers in a collection that uses the integer subscripts. |
| `PRIOR(n)`    | Returns the index number that precedes index n in a collection. |
| `NEXT(n)`     | Returns the index number that succeeds index n.              |
| `EXTEND`      | Appends one null element to a collection.                    |
| `EXTEND(n)`   | Appends n null elements to a collection.                     |
| `EXTEND(n,i)` | Appends **n** copies of the ith element to a collection.     |
| `TRIM`        | Removes one element from the end of a collection.            |
| `TRIM(n)`     | Removes **n** elements from the end of a collection.         |
| `DELETE`      | Removes all elements from a collection, setting COUNT to 0.  |
| `DELETE(n)`   | Removes the **nth** element from an associative array with a numeric key or a nested table. If the associative array has a string key, the element corresponding to the key value is deleted. If **n** is null, **DELETE(n)** does nothing. |
| `DELETE(m,n)` | Removes all elements in the range **m..n** from an associative array or nested table. If **m** is larger than **n** or if **m** or **n** is null, **DELETE(m,n)** does nothing. |

##### Collection Exceptions

| `COLLECTION_IS_NULL`      | You try to operate on an atomically null collection.         |
| ------------------------- | ------------------------------------------------------------ |
| `NO_DATA_FOUND`           | A subscript designates an element that was deleted, or a nonexistent element of an associative array. |
| `SUBSCRIPT_BEYOND_COUNT`  | A subscript exceeds the number of elements in a collection.  |
| `SUBSCRIPT_OUTSIDE_LIMIT` | A subscript is outside the allowed range.                    |
| `VALUE_ERROR`             | A subscript is null or not convertible to the key type. This exception might occur if the key is defined as a **PLS_INTEGER** range, and the subscript is outside this range. |

## [PL/SQL: Transactions Cheat Sheet](https://simplecheatsheet.com/pl-sql-transactions/)

##### Using COMMIT

The `commit `command permanently changes the data in the database.

```
Commit;
```

By default, **automatic commit for DML commands is off**. The automatic commit for DML commands can be set by using the following command

```
SET AUTOCOMMIT ON; 
-- and to turn it off
SET AUTOCOMMIT OFF;
```

##### Using ROLLBACK

```
ROLLBACK [TO SAVEPOINT < savepoint_name>]; 
```

##### Using SAVEPOINT

```
SAVEPOINT < savepoint_name >;
```

## [PL/SQL: Date & Time Cheat Sheet](https://simplecheatsheet.com/pl-sql-date-time/)

**Two classes of date and time related data types in PL/SQL**

- Datetime data types
- Interval data types

The Datetime data types 

- `DATE`
- `TIMESTAMP`
- `TIMESTAMP WITH TIME ZONE`
- `TIMESTAMP WITH LOCAL TIME ZONE`

The Interval data types are

- `INTERVAL YEAR TO MONTH`
- `INTERVAL DAY TO SECOND`

**Field Values for Datetime and Interval Data Types**

| Field Name        | Valid Datetime Values                                        | Valid Interval Values                                        |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `YEAR`            | -4712 to 9999 (excluding year 0)                             | Any nonzero integer                                          |
| `MONTH`           | 01 to 12                                                     | 0 to 11                                                      |
| `DAY`             | 01 to 31 (limited by the values of MONTH and YEAR, according to the rules of the calendar for the locale) | Any nonzero integer                                          |
| `HOUR`            | 00 to 23                                                     | 0 to 23                                                      |
| `MINUTE`          | 00 to 59                                                     | 0 to 59                                                      |
| `SECOND`          | 00 to 59.9(n), where 9(n) is the precision of time fractional secondsThe 9(n) portion is not applicable for DATE. | 0 to 59.9(n), where 9(n) is the precision of interval fractional seconds |
| `TIMEZONE_HOUR`   | -12 to 14 (range accommodates daylight savings time changes)Not applicable for DATE or TIMESTAMP. | Not applicable                                               |
| `TIMEZONE_MINUTE` | 00 to 59Not applicable for DATE or TIMESTAMP.                | Not applicable                                               |
| `TIMEZONE_REGION` | Not applicable for DATE or TIMESTAMP.                        | Not applicable                                               |
| `TIMEZONE_ABBR`   | Not applicable for DATE or TIMESTAMP.                        | Not applicable                                               |

**The Datetime Data Types and Functions**

- Datetime functions 

| `ADD_MONTHS(x, y);`     | Adds **y** months to **x**.                                  |
| ----------------------- | ------------------------------------------------------------ |
| `LAST_DAY(x);`          | Returns the last day of the month.                           |
| `MONTHS_BETWEEN(x, y);` | Returns the number of months between **x** and **y**.        |
| `NEXT_DAY(x, day);`     | Returns the datetime of the next *day* after **x**.          |
| `NEW_TIME;`             | Returns the time/day value from a time zone specified by the user. |
| `ROUND(x [, unit]);`    | Rounds **x**.                                                |
| `SYSDATE();`            | Returns the current datetime.                                |
| `TRUNC(x [, unit]);`    | Truncates **x**.                                             |

- Timestamp functions

| `CURRENT_TIMESTAMP();`                                       | Returns a TIMESTAMP WITH TIME ZONE containing the current session time along with the session time zone. |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `EXTRACT({ YEAR | MONTH | DAY | HOUR | MINUTE | SECOND } | { TIMEZONE_HOUR | TIMEZONE_MINUTE } | { TIMEZONE_REGION | } TIMEZONE_ABBR ) FROM x)` | Extracts and returns a year, month, day, hour, minute, second, or time zone from **x**. |
| `FROM_TZ(x, time_zone);`                                     | Converts the TIMESTAMP x and the time zone specified by time_zone to a TIMESTAMP WITH TIMEZONE. |
| `LOCALTIMESTAMP();`                                          | Returns a TIMESTAMP containing the local time in the session time zone. |
| `SYSTIMESTAMP();`                                            | Returns a TIMESTAMP WITH TIME ZONE containing the current database time along with the database time zone. |
| `SYS_EXTRACT_UTC(x);`                                        | Converts the TIMESTAMP WITH TIMEZONE x to a TIMESTAMP containing the date and time in UTC. |
| `TO_TIMESTAMP(x, [format]);`                                 | Converts the string x to a TIMESTAMP.                        |
| `TO_TIMESTAMP_TZ(x, [format]);`                              | Converts the string x to a TIMESTAMP WITH TIMEZONE.          |

**The Interval Data Types and Functions**

| `NUMTODSINTERVAL(x, interval_unit);` | Converts the number x to an INTERVAL DAY TO SECOND. |
| ------------------------------------ | --------------------------------------------------- |
| `NUMTOYMINTERVAL(x, interval_unit);` | Converts the number x to an INTERVAL YEAR TO MONTH. |
| `TO_DSINTERVAL(x);`                  | Converts the string x to an INTERVAL DAY TO SECOND. |
| `TO_YMINTERVAL(x);`                  | Converts the string x to an INTERVAL YEAR TO MONTH. |
