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
