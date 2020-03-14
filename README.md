# elastic-search


| Text   ->     | elastic-search -> | Analysis [Token + filter] -> |Inverted Index|
| ------------- |:-----------------:| --------------------------------:|----------|


#### Filter ####
1. Remove stop word (the)
2. Lower casing
3. Stemming (swimming ~ swim)
4. synonyms (thin ~ sjinny)

relation data base  | elastic-search |
----------| -------------|
Table       | Index      | 
Row      | Document    | 
Column   | Field        |

#### Indexing ####

```json
PUT /index/_doc/id

{
    "name": "value"
}
```

#### update ####

```json
POST /index/_doc/id/_update

{
    "doc" : {
        "name": "value"
    }
}
```

#### DELETE ####

```json
DELETE /index/_doc/id/
```

#### Retriving ####

```json
GET /index/_doc/id

```

###### Match all ######

```json
GET /index/_search
{
    "query": {
        "match_all": { "boost" : 1.2 }
    }
}
```
###### Match ######

```json
GET /index/_search
{
    "query": {
        "match" : {
            "message" : {
                "query" : "this is a test"
            }
        }
    }
}
```

### DSL List ###

1. match
2. match_all
3. exists
4. must
5. must_not
6. should
7. minimum_should_natch
8. multi_match
9. match_phrase
10. match_phrase_prefix
11. range 
12. sort ....etc

### Mapping ###

can create a Index with explict mapping

```json

PUT /my-index
{
  "mappings": {
    "properties": {
      "age":    { "type": "integer" },  
      "email":  { "type": "keyword"  }, 
      "name":   { "type": "text"  }     
    }
  }
}
```


