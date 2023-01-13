- Every key is a super key
- But every super key is not a key

A super key is a constraint on the key

For example if you have
```Student(studentId, name, major, gender, avgGPA)```

studentId is a key because two different students can't have the same key, it is also a student key
{studentID, name} is a super key but its not a key
Any combination would be a super key

Only one key can be a primary key while all others will be candidate keys.
