**Views help with logical data independence**

Retrieve data if it matches the description in the view

```
CREATE VIEW <view-name> AS <view-definition>

Example:
CREATE VIEW ParamountMovies AS
	SELCT movieTitle, movieYear
	FROM Movies
	WHERE studioName = "Paramount"
```

May ask queries on ParamountMovies *as if it were a table*
```
SELECT movieTitle FROM ParamountMovies WHERE movieYear = 1976
```

View is **NOT** a table stored in the Database, but definition is stored

TLDR: Its a pointer to a group

Modifying the table means the View is modified as well

## Advantages
 - Shorthand/encapsulation
	 - Shorthand for a concept that might involve a complicated query
 - Re-use
	 - Reuse the view as often as needed, even other people can use
 - Authorization
	 - May be granted access to the view, they don't know its a table or a view
	 - Do not know what tables contributed to the view
 - Logical data independence
	 - No need to rewrite query or application
	 - Even if table changes
