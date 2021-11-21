## We start by setting up a docker environment to use neo4j

Pull official docker image

`docker pull neo4j`{{execute}}

Start container

`docker run \
    --publish=7474:7474 --publish=7687:7687 \
    --volume=$HOME/neo4j/data:/data \
    --name=neo4jdwh \
    neo4j
`{{execute}}

Enter docker environment

`docker exec -it neo4jdwh bash`{{execute T2}}

