attendees 
----------
* mp
* ms
discussion/problems 
--------------------
* search for latest model? ```match (x..)-[]->(:MODEL)-[]->(:DIFF)-[]->(m:MODEL) return m` mit so vielen `(:MODEL)-[]->(:DIFF)-[]->``` wie moeglich. in neo4j leicht umzusetzen?
* wir wollen aber gar nicht immer das latest model... eventuell gibts da das gesuchte feature nicht mehr...
* nehmen wir an wir haben folgende 4 suchtreffer (```A9:r1` is model `A` in version `9` ranked with `r1```):
```
M1:r1, M2:r2, K1:r3, J7:r4
```
* dann wuerden wir es so gruppieren wollen um 3 suchtreffer zu erhalten:
```
M:max(r1,r2) {M1:r1, M2:r2}, K1:r3, J7:r4
```
* is das korrekt?

questions/issues 
-----------------
* muessen wir ranking updaten?
* wo ist suche und ranking implementiert? -> masymos?
* morre muss wohl wirklich angefasst werden, um die neue struktur der suchergebnisse wieder zu spiegeln..?