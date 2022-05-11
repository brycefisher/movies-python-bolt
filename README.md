Neo4j Basics
-------------


Start the database:

```sh
docker run \
    --publish=7474:7474 --publish=7687:7687 \
    --volume=$HOME/neo4j/data:/data \
    --net=host \
    neo4j
```

Open the browser: http://localhost:7474/browser/

Default credentials:
 * Username: `neo4j`
 * Password: `neo4j`

Start Python server:

```sh
cd ~/Desktop
python3 -m http.server
```

Use Cypher in Neo4j shell to import CSV file with minimal set of words:

```cypher
LOAD CSV WITH HEADERS FROM "http://bff-g7-7500:8000/words.csv" AS row
CREATE (w:Word)
SET w = row
```

Query to see the words exist:

```cypher
MATCH (w:Word) RETURN w.title
```
