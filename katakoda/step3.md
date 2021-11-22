## Import the data in neo4j

Before we start working with the database a few words about what Neo4j is and why it can be useful for studies.

Neo4j is the leading graph datanase and offers additional tools such as a browser interface to easily visualize data.

As depicted below graph databases are part of nosql databases.
![Types of database](./Screeenshot_Folien_Tools.png)
Andreas Buckenhofer. Lecture @DHBW: Data Warehouse. Lecture slides. 02 Tools. DHBW Stuttgart, delivered October 2021.

For this example we will use the cypher shell to work with Neo4j. Cypher shell is the basic cli tool Neo4j offers for interaction with the database. The shell can be opened with the command cypher-shell. A user and password need to be added. After first accessing the database a new password has to be set which you can chose freely.

`cypher-shell -u neo4j -p neo4j`{{execute}}
Change of password is necessary

Load CSV data
This will model every line of the CSV file as a new person. Relations between every participant and the other columns will be created.
The line greatest fear will not be imported to keep the example simple.


![Structure of graph stores](./Screeenshot_Folien_graphmodel.png)
Andreas Buckenhofer. Lecture @DHBW: Data Warehouse. Lecture slides. 02 Tools. DHBW Stuttgart, delivered October 2021.

`LOAD CSV WITH HEADERS FROM 'file:///FearStudyData.csv' AS line CREATE (l:Person {Name: randomUUID()}) MERGE (n:Fear {Name:line.Fear}) MERGE (l) -[:fears {fears:line.Fear}]-> (n) MERGE (m:Impact {Name:line.Impact}) MERGE (l) -[:impact {Name:line.Impact}]-> (m) MERGE (o:ExperiencedInThePast {Name:line.Past}) MERGE (l) -[:past {past:line.Past}]-> (o) MERGE (p:Encounter {Name:line.Encounter}) MERGE (l) -[:encountered {encountered:line.Encounter}]-> (p) MERGE (q:Overcome {Name: COALESCE(line.Overcome, 'NA')}) MERGE (l) -[:overcome {overcome: COALESCE(line.Overcome, 'NA')}]-> (q) MERGE (r:Embarrassed {Name:line.Embarrassed}) MERGE (l) -[:embarrassed {embarrassed:line.Embarrassed}]-> (r);`{{execute}}


