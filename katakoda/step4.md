The last step of this example is a demonstration query.

For our purpose we will try to determine if thinking it is possible to overcome a fear could be related to being embarrassed of the fear.
Please keep in mind that this pilot study does not deliver a sufficient amount of data to get realistic results.

We first query the number of people who think they can overcome their fear. The query is separated into people who are also embarrassed of their fear and the number of people who are not:

MATCH (p:Person)-[q:overcome]->(f) MATCH (p)-[r:embarrassed]->(g) WHERE q.overcome="Yes" AND r.embarrassed="Yes" RETURN COUNT(p){{execute}}

MATCH (p:Person)-[q:overcome]->(f) MATCH (p)-[r:embarrassed]->(g) WHERE q.overcome="Yes" AND r.embarrassed="No" RETURN COUNT(p){{execute}}


Now we request the numbers of people who do not think they can overcome their fear:

MATCH (p:Person)-[q:overcome]->(f) MATCH (p)-[r:embarrassed]->(g) WHERE q.overcome="No" AND r.embarrassed="Yes" RETURN COUNT(p){{execute}}

MATCH (p:Person)-[q:overcome]->(f) MATCH (p)-[r:embarrassed]->(g) WHERE q.overcome="No" AND r.embarrassed="No" RETURN COUNT(p){{execute}}


By comparing the numbers we find that there does not seem to be a connection between believing in overcoming a fear and being embarrassed of it.

Question: Why do we need to request all four results? If we know that there were 79 people joining the survey could we not have computed two of the queries by adding up values?(Result on step 5)

