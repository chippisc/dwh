Pull official docker image
`docker pull neo4j`{{execute}}

Start container
`docker run \
    --publish=7474:7474 --publish=7687:7687 \
    --volume=$HOME/neo4j/data:/data \
    neo4j
`{{execute}}
Enter docker environment
`docker exec -it testneo4j bash`{{execute}}

Open cypher shell
`cypher-shell -u neo4j -p neo4j`{{execute}}
Change of password is necessary

