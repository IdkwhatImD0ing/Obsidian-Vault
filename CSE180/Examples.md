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