To get started using Neo4j as fast and easy as possible we use ![https://hub.docker.com/_/neo4j](the official Neo4j docker image).

We can pull the docker image by typing

`docker pull neo4j`{{execute}}

After successfully downloading the container we can run it using

`docker run \
    --publish=7474:7474 --publish=7687:7687 \
    --volume=$HOME/neo4j/data:/data \
    --name=neo4jdwh \
    neo4j
`{{execute}}

The parameters add a name to the container for easy reference, a volume for neo4j to be able to store data aswell as two published ports. The ports grant HTTP and Bolt access to the database.

For Neo4j to be able to use the csv file we need to copy it to the container. Neo4j by standard uses the folder ```neo4j/import/``` to access files so this is the location we want to copy our file to.
We copy the csv file to the container by using docker cp:

`docker cp ./FearStudyData.csv neo4jdwh:/var/lib/neo4j/import/FearStudyData.csv`{{execute T2}}

After copying the file to the container we are set up to enter the container. To open a new interactive shell in the container we run the following command:

`docker exec -it neo4jdwh bash`{{execute}}

