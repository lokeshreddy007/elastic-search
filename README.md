# elastic-search

To start 

```json

// from elasticsearch floder
.\bin\elasticsearch.bat

// from kibana floder
.\bin\kibana.bat

```

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


### Create Index using Curl ###

curl -X PUT "localhost:9200/twitter?pretty"


check links

http://www.cplusplus.com/forum/general/89488/
https://curl.haxx.se/download.html
https://bintray.com/artifact/download/vszakats/generic/curl-7.69.1-win64-mingw.zip

copy bin, lib, inlcude to Qt MGWin floder


// Qt Lib in pro file
LIBS += C:/Qt/Qt5.12.3/5.12.3/mingw73_64/lib/libcurl.a
LIBS += C:/Qt/Qt5.12.3/5.12.3/mingw73_64/lib/libcurldll.a
INCLUDEPATH += C:/Qt/Qt5.12.3/5.12.3/mingw73_64/lib

```json

POST /testing/
{
     "location" : "40.175223,-161.785881",
    "Sold": 90,
    "Remaining": 65,
    "Fruit": "apple",
"2020-03-09T18:27:00"
}
```

```json
{
    PUT /testing
{
  "mappings": {
    "properties": {
        "timestamp" : {
          "type" : "date"
        },
      "age":    { "type": "integer" },  
      "email":  { "type": "keyword"  }, 
      "name":   { "type": "keyword"  },
        "location" : {
          "type" : "geo_point"
        },
      "company":   { "type": "keyword"  },
        "balance":    { "type": "float" },  
      "remaining":  { "type": "integer"}, 
      "Fruit":   { "type": "keyword"  },
       "sold":  { "type": "integer"  }
    }
  }
}
}
```

```json
      {
        "_index" : "kibana_sample_data_flights",
        "_type" : "_doc",
        "_id" : "ufkV-HABFiMMzHrskQuH",
        "_score" : 1.2,
        "_source" : {
          "FlightNum" : "9HY9SWR",
          "DestCountry" : "AU",
          "OriginWeather" : "Sunny",
          "OriginCityName" : "Frankfurt am Main",
          "AvgTicketPrice" : 841.2656419677076,
          "DistanceMiles" : 10247.856675613455,
          "FlightDelay" : false,
          "DestWeather" : "Rain",
          "Dest" : "Sydney Kingsford Smith International Airport",
          "FlightDelayType" : "No Delay",
          "OriginCountry" : "DE",
          "dayOfWeek" : 0,
          "DistanceKilometers" : 16492.32665375846,
          "timestamp" : "2020-03-09T00:00:00",
          "DestLocation" : {
            "lat" : "-33.94609833",
            "lon"
          }
        }
      }
```

```json
POST /fruits/_bulk
{ "index": {} }
{ "sold" : 12, "remaining" : 73,  "location" : "-70.062049,57.48776",  "timestamp" : "2020-03-09T18:58:00"  , "Fruit" : "orange"}
{ "index": {} }
{ "sold" : 34, "remaining" : 34,  "location" : "-70.062049,57.48776",  "timestamp" : "2020-03-09T18:58:00"  , "Fruit" : "apple"}
{ "index": {} }
{ "sold" : 5, "remaining" : 28,  "location" : "-70.062049,57.48776",  "timestamp" : "2020-03-09T18:58:00"  , "Fruit" : "banana"}\
```

```json
PUT /fruits/_doc/11
{
    "sold" : 12, 
    "remaining" : 73,  
    "location" : "-70.062049,57.48776",  
    "timestamp" : "2020-03-09T18:58:00"  , 
    "Fruit" : "orange"
}
```

```json

GET /fruits/_search 
{
  "size" : 20,
  "query" : {
  
  "match_all" : {}
  }
}
```