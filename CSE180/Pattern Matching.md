## Like

'%' Matches one or more characters
'\_' Matches exactly one arbitary character

Jurassic% matches: Jurassic, JurassicW, Jurassic World... etc

Jurassic_ matches: Jurassic1, but **not** Jurassic12

## Escape

Lets you choose an escape character
For example Like '|\%\%|\_'
This matches anything that begins with a percent and ends with an underscore

## Order By

Orders the results returned by the sql call
For example SELECT * FROM R1, ORDER BY <list of attributes\>

Either ASC or DESC
NULL will always probably be the smallest or largest value

## Comparing
You can compare almost any constant in  with eadh other
 - DATE
 - TIME
 - TIMESTAMP
 - INTERVAL

3 Values: True, False, Unknown
Unique Truth Table

Unknown is very similar to False but not the same
Examaple,  Not Unknown != Not False
