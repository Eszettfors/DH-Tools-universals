Query to test U2

MATCH (language:Language)-[:HAS_VALUE]->(pre:Value {id: 'Prepositions'})
MATCH (language:Language)-[:HAS_VALUE]->(gn:Value {id: 'Genitive-Noun'})
RETURN COUNT(*);

/// change value according to need


------
loading queries for all features



LOAD CSV WITH HEADERS FROM "file:///85A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);


LOAD CSV WITH HEADERS FROM "file:///86A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);


LOAD CSV WITH HEADERS FROM "file:///30A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);

LOAD CSV WITH HEADERS FROM "file:///44A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);


LOAD CSV WITH HEADERS FROM "file:///49A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);

LOAD CSV WITH HEADERS FROM "file:///81A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {id: row.Value, parameter: row.Parameter_ID})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);


LOAD CSV WITH HEADERS FROM "file:///69A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);


LOAD CSV WITH HEADERS FROM "file:///81B.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);

LOAD CSV WITH HEADERS FROM "file:///87A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);


LOAD CSV WITH HEADERS FROM "file:///88A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);

LOAD CSV WITH HEADERS FROM "file:///89A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);


LOAD CSV WITH HEADERS FROM "file:///90A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);

LOAD CSV WITH HEADERS FROM "file:///92A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);


LOAD CSV WITH HEADERS FROM "file:///93A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);

LOAD CSV WITH HEADERS FROM "file:///97A.csv" AS row
MERGE (language:Language {id: row.Language_ID, name:row.Name})
MERGE (value:Value {parameter: row.Parameter_ID, id: row.Value})
MERGE (family:Family {name: row.Family})
MERGE (language)-[:HAS_VALUE]->(value)
MERGE (language)-[:BELONGS_TO]->(family);


---
Find all languages belonging to a language family:
match (language:Language)-[:BELONGS_TO]->(family:Family {name: 'Indo-European'})
MATCH (language)-[:HAS_VALUE]->(value:Value)
return language, family, value