## Import the data in neo4j

Open cypher shell
`cypher-shell -u neo4j -p neo4j`{{execute}}
Change of password is necessary


Load CSV data
This will model every line of the CSV file as a new person. Relations between every participant and the other columns will be created.
The line greatest fear will not be imported to keep the example simple.

`LOAD CSV WITH HEADERS FROM 'file:///FearStudyData.csv' AS line CREATE (l:Person {Name: randomUUID()}) MERGE (n:Fear {Name:line.Fear}) MERGE (l) -[:fears {fears:line.Fear}]-> (n) MERGE (m:Impact {Name:line.Impact}) MERGE (l) -[:impact {Name:line.Impact}]-> (m) MERGE (o:ExperiencedInThePast {Name:line.Past}) MERGE (l) -[:past {past:line.Past}]-> (o) MERGE (p:Encounter {Name:line.Encounter}) MERGE (l) -[:encountered {encountered:line.Encounter}]-> (p) MERGE (q:Overcome {Name: COALESCE(line.Overcome, 'NA')}) MERGE (l) -[:overcome {overcome: COALESCE(line.Overcome, 'NA')}]-> (q) MERGE (r:Embarrassed {Name:line.Embarrassed}) MERGE (l) -[:embarrassed {embarrassed:line.Embarrassed}]-> (r);`{{execute}}
