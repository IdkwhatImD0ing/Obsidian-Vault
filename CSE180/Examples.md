## Schema:
Let us assume we have the following database schema with five relation schemas, with primary keys underlined. 
- Movies(movieTitle, movieYear, length, genre, studioName, producerC#) 
- StarsIn(movieTitle, movieYear, starName) 
- MovieStar(starName, address, gender, birthdate) 
- MovieExec(execName, address, cert#, netWorth) 
- Studio(studioName, address, presC#)

### Who were the male stars in the 2022 movie Avatar?

SELECT * FROM MovieStar