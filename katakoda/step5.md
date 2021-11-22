If you closely inspected the given query we used to insert the data you have noticed that we used a function called COALESCE. Coalesce takes an argument list and returns the first value which is not null.[2] So the given data contains missing data which would lead to wrong results if we had added up the numbers too early. Instead we can know guess how many people did not give an answer. 

>>Can you find the correct query to check?<<
()MATCH (p:Person)-[q:overcome]->(f) MATCH (p)-[r:embarrassed]->(g) WHERE q.embarrassed="NA" RETURN COUNT(p){{execute}}
(*)MATCH (p:Person)-[q:overcome]->(f) MATCH (p)-[r:embarrassed]->(g) WHERE q.overcome="NA" RETURN COUNT(p){{execute}}
()MATCH (p:Person)-[q:overcome]->(f) MATCH (p)-[r:embarrassed]->(g) WHERE r.overcome="NA" RETURN COUNT(p){{execute}}
()MATCH (p:Person)-[q:overcome]->(f) MATCH (p)-[r:embarrassed]->(g) WHERE r:overcome="NA" RETURN COUNT(p){{execute}}
()MATCH (p:Person)-[q:overcome]->(f) MATCH (p)-[r:embarrassed]->(g) WHERE q:overcome="NA" RETURN COUNT(p){{execute}}
