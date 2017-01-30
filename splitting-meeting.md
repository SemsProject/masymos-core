goals 
======
understand masymos 
-------------------
* ```*.main``` batch stuff
* ```*.extractor``` extractors for SBML, CellML, SedML, Owl, XML (=just throws not possible)
 * owl to neo4j is old rebekka stuff -> can go
* ```*.data``` : wrapper for fields (to eg. generate JSON?)
 * fixed structure for info ron wants to have
 * persons and publication
* ```*.database``` actual database administration
 * singleton instance (only one instance)
 * ```Manager```:
  * "thinks about it" comment?
  * for ever index and every feature/filed there is an analyser, see ```*.analyser```
  * execution engine (runs cypher stuff)
 * ```ModelInserter` / `ModelLookup```: connection to MartinP, crawling other model repos and import into db
* ```*.database.traverse``` go from search hit to model node etc
 * for models and sedml
* ```*configuration```
 * ```Config```: basic static stuff, saved config files
 * ```Properties`, `Relation`, `NodeLabel```: enums for all labels, properties, etc
* ```*analyser```
 * all have a name, 
 * analyse search terms
 * eg. ```lowercasekeywordanalyser```:
  * info missing?
  * preprocessing before goes into index: split by whitespace, transform into lower case
* ```*annotation```
 * ```resolver```: query miriam web service -> resolve URNs to URLs
 * ```fetch```: reads text content on the url and stores it in db
* ```*grouping``` (hehe, was done by rebekka -> ron)
 * clustering of ontology terms
* ```*query```
 * ```enumerator```: just enumerating the "strings"
 * ```results```: for each index -> how the results are handled
  * sedml has problems? nothing in there, written by rebekka
  * how to handle results sets?
  * important ```equals``` function -> compare result sets
 * ```structure``` is something ron is trying -> skipping
 * interfaces: all information that is needed if you want to implement an interface
 * ```types```, eg person
  * analyser, fields, index defined
  * lucene specific formats
  * retrieve/ModelResultByPerson
 * ```queryadapter```
  * they changed something in lucene code...? -> should we implement that natively?
* ```util```: stuff that fits nowhere else
 * assign -> cant remember -> was for rebekka -> hungarian?
 * cmeta -> done by tommy
 * hungarian -> fancy algorithm -> wikiedia
 * identifier converter
 * etc
 * ontology factory -> include owl
 * ontology util -> distance, shorted paths etc
 * resultsetcomparator -> mariam is working on -> thats useful for the diff
 * structure query -> actually only comments



"much creepy code" (cite r. henkel 2015)


understand diff 
----------------
* ```*diff```:
 * ```diffexecuter```: commandozeilen tool
  * executer: sucher doc ohne diff, 5 threads in parallel
 * ```diffjob```: eigentliche arbeit: kriegt 2 knoten, erzeugt diff, speichert diff in datenbank:
  * iteriere ueber diffs
  * hole old/new xpath -> doc nodes
  * inherit: go up in tree to find a doc node that has representation in db
 * ```diffutil``` traversiert graph
 * ```data``` unspannend, only id kram

TODO:
* HAS_DIFF in eine richtung umbenennen


optimize 
---------
* 



split into modules 
-------------------
modules:
```
     - CellML -        - server plugin
CORE - SBML   - bundle - cli
     - SedML  -
```


create a roadmap 
-----------------