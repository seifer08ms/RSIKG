# RSIKG

`rsikg.tar` is the compressed data.
## Property graph analysis and applications
Importing data into Neo4j
```
CALL n10s.graphconfig.init();
CREATE CONSTRAINT n10s_unique_uri for (r:Resource) require r.uri IS UNIQUE;
CALL n10s.graphconfig.set({ handleVocabUris: "IGNORE" });
CALL n10s.rdf.import.fetch('file:///rsikg_mapping_mod.nt', 'N-Triples');
```

Analysis of the shortest path between two sensors
```
MATCH (p1:sensor {sensor_Name:"GLI"}),(p2:sensor{sensor_Name:"SPOT 6"}),
p=shortestpath((p1)-[*..10]-(p2))
RETURN p 
```
