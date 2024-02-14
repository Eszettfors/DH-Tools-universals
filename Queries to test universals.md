Universal 2: “In languages with prepositions, the genitive almost always follows the governing noun, while in languages with postpositions it almost always precedes.”

WALS features used: 85A, 86A

Queries:
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id: 'Prepositions'})
MATCH (language:Language)-[:HAS_VALUE] ->(ng:Value {id: 'Noun-Genitive'})
RETURN COUNT(*);


MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id: 'Postpositions'})
MATCH (language:Language)-[:HAS_VALUE] ->(ng:Value {id: 'Noun-Genitive'})
RETURN COUNT(*);


MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id: 'Postpositions'})
MATCH (language:Language)-[:HAS_VALUE] ->(ng:Value {id: ‘Genitive-Noun'})
RETURN COUNT(*);


MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id: 'Prepositions'})
MATCH (language:Language)-[:HAS_VALUE] ->(ng:Value {id: ‘Genitive-Noun'})
RETURN COUNT(*);

---------------------

Universal 3: “Languages with dominant VSO order are always prepositional.”

WALS features used: 81A, 85A, 95A 

Queries:
MATCH (language:Language)-[:HAS_VALUE]->(vso:Value {id: 'VSO'})
MATCH (language:Language)-[:HAS_VALUE] ->(pre:Value {id: 'Prepositions'})
RETURN COUNT(*);


MATCH (language:Language)-[:HAS_VALUE]->(vso:Value {id: 'VSO'})
MATCH (language:Language)-[:HAS_VALUE] ->(pos:Value)
WHERE pos.id IN ['Postpositions', 'Inpositions', 'No dominant adposition order', 'No adpositions']
RETURN COUNT(*);

--------------------

Universal 4: “With overwhelmingly greater than chance frequency, languages with normal SOV order are postpositional.”
WALS features used: 81A, 85A

Queries:
MATCH (language:Language)-[:HAS_VALUE]->(sov:Value {id: 'SOV'})
MATCH (language:Language)-[:HAS_VALUE] ->(pos:Value {id: 'Postpositions'})
RETURN COUNT(*)

MATCH (language:Language)-[:HAS_VALUE]->(vso:Value {id: 'SOV'})
MATCH (language:Language)-[:HAS_VALUE] ->(pos:Value)
WHERE pos.id IN ['Postpositions', 'Inpositions', 'No dominant adposition order', 'No adpositions']
RETURN COUNT(*);

-------------------


Universal 5: “If a language has dominant SOV order and the genitive follows the governing noun, then the adjective likewise follows the noun.”

WALS features used: 81A, 86A

Query:
MATCH (language:Language)-[:HAS_VALUE]->(sov:Value {id: 'SOV'})
MATCH (language:Language)-[:HAS_VALUE] ->(ng:Value {id: 'Noun-Genitive'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(sov:Value {id: 'SOV'})
MATCH (language:Language)-[:HAS_VALUE] ->(ng:Value {id: 'Noun-Genitive'})
MATCH (language:Language)-[:HAS_VALUE] ->(na:Value {id: 'Noun-Adjective'})
RETURN COUNT(*)

----------------

Universal 9: “With well more than chance frequency, when question particles or affixes are specified in position by reference to the sentence as a whole, if initial, such elements are found in prepositional languages, and, if final, in postpositional.”

WALS features used: 85A, 92A, 93A

Queries:
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id: 'Postpositions'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Initial'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id: 'Postpositions'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: ‘Final})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id: 'Prepositions'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Initial'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id: 'Postpositions'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Final'})
RETURN COUNT(*)


----------------------------


Universal 11: “Inversion of statement order so that verb precedes subject occurs only in languages where the question word or phrase is normally initial. This same inversion occurs in yes–no questions only if it also occurs in interrogative word questions.”

WALS features used: 81B, 92A, 93A

Queries:
MATCH (language:Language)-[:HAS_VALUE]->(WO:Value)
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value)
WHERE WO.id IN ['SVO_or_VSO', 'SVO_or_VOS', 'SOV_or_OVS'] AND qp.id IN ['Initial']
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(WO:Value)
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value)
WHERE WO.id IN ['SVO_or_VSO', 'SVO_or_VOS', 'SOV_or_OVS'] AND qp.id IN ['Final', 'Second_position', 'Other_position', 'In_either_of_the_two_positions']
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(WO:Value)
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value)
WHERE WO.id IN ['SVO_or_VSO', 'SVO_or_VOS', 'SOV_or_OVS'] AND qp.id IN [’Initial_interrogative_phrase’]
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(WO:Value)
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value)
WHERE WO.id IN ['SVO_or_VSO', 'SVO_or_VOS', 'SOV_or_OVS'] AND qp.id IN [’Not_initial_interrogative_phrase’]
RETURN COUNT(*)


-----------------


Universal 12: “If a language has dominant order VSO in declarative sentences, it always puts interrogative words or phrases first in interrogative word questions; if it has dominant order SOV in declarative sentences, there is never such an invariant rule.”

WALS features used: 81B, 92A, 93A
Queries:
MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'VSO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Initial_interrogative_phrase'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'VSO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Not_initial_interrogative_phrase'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'VSO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Not_initial_interrogative_phrase'})
RETURN COUNT(*)

MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'VSO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Initial'})
RETURN COUNT(*)

MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'VSO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Final'})
RETURN COUNT(*)

MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'SVO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Initial_interrogative_phrase'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'SVO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Not_initial_interrogative_phrase'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'SVO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Not_initial_interrogative_phrase'})
RETURN COUNT(*)

MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'SVO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Initial'})
RETURN COUNT(*)

MATCH (language:Language)-[:HAS_VALUE]->(WO:Value{id: 'SVO'})
MATCH (language:Language)-[:HAS_VALUE] ->(qp:Value {id: 'Final'})
RETURN COUNT(*)

-----------------------


Universal 17: “With overwhelmingly more than chance frequency, languages with dominant order VSO have the adjective after the noun.”

WALS features used: 81A, 87A, 97A

Queries:
MATCH (language:Language)-[:HAS_VALUE]->(WO:Value {id:'VSO'})
MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:'Noun-Adjective'})
RETURN COUNT(*)

MATCH (language:Language)-[:HAS_VALUE]->(WO:Value {id:'VSO'})
MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:Adjective-Noun'})
RETURN COUNT(*)

-------------------------------

Universal 18: “When the descriptive adjective precedes the noun, the demonstrative and the numeral, with overwhelmingly more than chance frequency, do likewise.”

WALS features used: 87A, 88A, 89A

Queries:
MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:'Adjective-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(den:Value {id:'Demonstrative-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(num:Value {id:'Numeral-Noun'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:'Adjective-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(den:Value {id:'Demonstrative-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(num:Value {id:Noun-Numeral'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:'Adjective-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(den:Value {id:Noun-Demonstrative'})
MATCH (language:Language)-[:HAS_VALUE]->(num:Value {id:'Noun-Numeral'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:'Adjective-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(den:Value {id:'Noun-Demonstrative'})
MATCH (language:Language)-[:HAS_VALUE]->(num:Value {id:'Numeral-Noun'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:’Noun-Adjective'})
MATCH (language:Language)-[:HAS_VALUE]->(den:Value {id:'Demonstrative-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(num:Value {id:'Numeral-Noun'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:’Noun-Adjective'})
MATCH (language:Language)-[:HAS_VALUE]->(den:Value {id:'Demonstrative-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(num:Value {id:Noun-Numeral'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:'Noun-Adjective'})
MATCH (language:Language)-[:HAS_VALUE]->(den:Value {id:Noun-Demonstrative'})
MATCH (language:Language)-[:HAS_VALUE]->(num:Value {id:'Noun-Numeral'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(na:Value{id:'Adjective-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(den:Value {id:'Noun-Demonstrative'})
MATCH (language:Language)-[:HAS_VALUE]->(num:Value {id:'Numeral-Noun'})
RETURN COUNT(*)

-----------------------


Universal 24: “U24 If the relative expression precedes the noun either as the only construction or as an alternate construction, either the language is postpositional, or the adjective precedes the noun or both.”

WALS features used: 85A, 87A, 90A

Queries:
MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Postpositions'})
MATCH (language:Language)-[:HAS_VALUE]->(an:Value {id:'Adjective-Noun'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Postpositions'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Prepositions'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Postpositions'})
MATCH (language:Language)-[:HAS_VALUE]->(an:Value {id:'Adjective-Noun'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(an:Value {id:'Adjective-Noun'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(an:Value {id:'Noun-Adjective'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Postpositions'})
MATCH (language:Language)-[:HAS_VALUE]->(an:Value {id:'Adjective-Noun'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Postpositions'})
MATCH (language:Language)-[:HAS_VALUE]->(an:Value {id:'Noun-Adjective'})
RETURN COUNT(*)

MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Prepositions'})
MATCH (language:Language)-[:HAS_VALUE]->(an:Value {id:'Adjective-Noun'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE] ->(rela:Value{id:'Relative clause-Noun'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Prepositions'})
MATCH (language:Language)-[:HAS_VALUE]->(an:Value {id:'Noun-Adjective'})
RETURN COUNT(*)

-----------------------


Universal 27: “If a language is exclusively suffixing, it is postpositional; if it is exclusively prefixing, it is prepositional.”

WALS features used: 26A, 85A

Queries:
MATCH (language:Language)-[:HAS_VALUE]->(suf:Value{id:'Strongly suffixing'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Prepositions'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(suf:Value{id:'Strongly suffixing'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Postpositions'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(suf:Value{id:'Strong prefixing'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Prepositions'})
RETURN COUNT(*)


MATCH (language:Language)-[:HAS_VALUE]->(suf:Value{id:'Strongly prefixing'})
MATCH (language:Language)-[:HAS_VALUE]->(pos:Value {id:'Postpositions'})
RETURN COUNT(*)


--------------------------------


Universal 41: “If in a language the verb follows both the nominal subject and nominal object as the dominant order, the language almost always has a case system.”

WALS features used: 49A, 81A

Queries:
MATCH (language:Language)-[:HAS_VALUE] ->(wo:Value)
MATCH (language:Language)-[:HAS_VALUE] ->(cas:Value)
WHERE cas.id IN ['No morphological case-marking’] AND wo.id IN ['SOV', 'OSV']
RETURN COUNT(*)

MATCH (language:Language)-[:HAS_VALUE] ->(wo:Value)
MATCH (language:Language)-[:HAS_VALUE] ->(cas:Value)
WHERE cas.id IN ['2 cases', '3 cases','4 cases', '5 cases', '6-7 cases','8-9 cases','10 or more cases','Exclusively borderline case-marking'] AND wo.id IN ['SOV', 'OSV']
RETURN COUNT(*)
