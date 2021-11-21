## Import the data in neo4j

Open cypher shell
`cypher-shell -u neo4j -p neo4j`{{execute}}
Change of password is necessary


Load CSV data
`LOAD CSV FROM 'file:///FearStudyData.csv' AS line CREATE (:Fear {name: line[1]});`{{execute}}

`LOAD CSV FROM 'file:///FearStudyData.csv' AS line CREATE (:Fear {fear: line[1], greatest: line[2], impact:toInteger(line[3]), past: toBoolean(line[4]), Encounter: toInteger(line[5]), overcome: toBoolean(line[6]), embarrassed: toBoolean(line[7])});`{{ecexute}}
