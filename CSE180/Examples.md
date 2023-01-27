## Schema:
Let us assume we have the following database schema with five relation schemas, with primary keys underlined:

- Movies(movieTitle, movieYear, length, genre, studioName, producerC#) 
- StarsIn(movieTitle, movieYear, starName) 
- MovieStar(starName, address, gender, birthdate) 
- MovieExec(execName, address, cert#, netWorth) 
- Studio(studioName, address, presC#)

### Who were the male stars in the 2022 movie Avatar?
```
SELECT ms.StarName FROM MovieStar ms, StarsIn si 
WHERE ms.genter = 'M'
AND si.movieYear = 2022
AND si.moveTitle = 'Avatar'
AND ms.starName = si.starName 
```

Last line is required: Or else the tuples will have no relationship to each other
Last line basically says this person starred in the movie


### Find the id and name of each customer who did some activity on 01/07/21

```
Select c.cid, c.name FROM Customers c, Activities a
WHERE a.day = DATE '01/07/21' AND a.cid = c.cid 
```

No duplicate version:
```
SELECT c.cid, c.cname FROM Customers c
WHERE c.cid IN (SELECT a.cid FROM Activities
				WHERE a.day = DATE '01/07/21')
```
Can also replace ```IN``` with ```= ANY```

### Find the id and name who did not do an activity
```
SELECT c.cid, c.cname FROM Customers c
WHERE c.cid NOT IN (SELECT a.cid FROM Activities
				WHERE a.day = DATE '01/07/21')
```