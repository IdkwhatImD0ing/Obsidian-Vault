## Keys

- Every key is a super key
- But every super key is not a key

A super key is a constraint on the key

For example if you have
```Student(studentId, name, major, gender, avgGPA)```

studentId is a key because two different students can't have the same key, it is also a student key
{studentID, name} is a super key but its not a key
Any combination would be a super key

Only one key can be a primary key while all others will be candidate keys.

## Elements

If D1 has n1 elements, and Dn has n elements
What is the Cartesian Product of D1 x ... x Dn?
Willl be n1 x n2 ... x n

## Modifying Tables

To add a column, 
```ALTER TABLE MovieStar ADD phone CHAR(16);```

To remove a column
```ALTER TABLE MovieStar DROP birthdate;```

### Default Values
Default Value: Gives a column a default value if none is given

If a row is inserted and the attribute has a value, then that value would be set
If a row is inserted and the attribute is not given and there is a default value, the attribute would be set as default value
If a row is inserted and the attribute is not given and there is no default value and the attribute can be null, then the attribute is set as null
Else, throw an error

### Primary Keys
Shorthand, where one attribute is primary key:
```CREATE TABLE (name CHAR(30) PRIMARY KEY)```

Multiple attributes in primary key
```CREATE TABLE (name CHAR(30), phoneNumber INTEGER, PRIMARY KEY (name, phoneNumber))```

Can make an attribute UNIQUE, but is not the same as Primary Key
Can do it shorthand or for multiple attributes the same as Primary Key

## Subqueries

A subquery is a query that contains another query.

For example SELECT * FROM E1 where a = (SELECT * FROM E2)