# d:swarm Q'and'A session for UvA

samples for d:swarm Q'and'A session for UvA

## Data Resources

- JSON: https://github.com/dswarm/dswarm/blob/builds/unstable/controller/src/test/resources/controller_bib-record-marc.json
- XML: https://github.com/dswarm/dswarm/blob/builds/unstable/controller/src/test/resources/test.oai-pmh_marcxml.xml
- CSV: https://github.com/dswarm/dswarm/blob/builds/unstable/controller/src/test/resources/csvtasks/IEEE-Proceedings_Titelliste.sample.csv

## Data Models

(content)

write data model to local Data Hub (e.g.)

    curl -H "Content-Type:multipart/mixed" -F "content=@request.json; type=application/json" -F "content=@test-gdm.json; type=application/octet-stream" -X POST http://localhost:7474/graph/gdm/put -i -v
    
example for metadata of the request (```request.json```)
    
    {
        "data_model_uri": "http://data.slub-dresden.de/datamodel/DataModel-cf998267-392a-4d87-a33a-88dd1bffb016/data",
        "deprecate_missing_records": "false",
        "record_class_uri": "http://purl.org/ontology/bibo/Document",
        "enable_versioning": "false"
    }
    
(see the related ```write.gdm.request.[..].json``` files)
    
### Input Data Models (sources)

- JSON: https://github.com/zazi/UvA-Q-and-A/blob/master/datamodel.ef4dc7cc-1fa4-d418-fa83-c43c843423c7.gdm.json
- XML: https://github.com/zazi/UvA-Q-and-A/blob/master/datamodel.95184270-8e10-463c-f515-9b4d585cb705.gdm.json
- CSV: https://github.com/zazi/UvA-Q-and-A/blob/master/datamodel.c4ab3fd6-d37f-2285-f0e4-079595482647.gdm.json
  
## Projects (incl. Mappings)

- JSON: https://github.com/zazi/UvA-Q-and-A/blob/master/project.7f266a87-d01e-2508-28eb-06bfb017744f.json
- XML:
 - XML example project: https://raw.githubusercontent.com/zazi/UvA-Q-and-A/master/project.50e4c934-1e45-a928-8c00-86d0da28cfff.json
 - XML example project 2: https://github.com/zazi/UvA-Q-and-A/blob/master/project.7602def8-1f58-fbec-3b3a-104387c4fd44.json
 - XML example project 3: https://github.com/zazi/UvA-Q-and-A/blob/master/project.bf48af2f-1b5b-3410-984a-0ca773c53930.json
 - XML example project 4: https://github.com/zazi/UvA-Q-and-A/blob/master/project.9b475caf-cad1-ce8c-35b5-815becd60fc3.json
- CSV: https://github.com/zazi/UvA-Q-and-A/blob/master/project.d60ee1d3-ac0b-16e5-6050-a138299485d2.json

push project to (another) d:swarm instance

1. robust import

    ```
        curl -v -XPOST -H "Content-Type: application/json"  -d"@[FILE NAME].json" http://[HOSTNAME OR IP TO YOUR D:SWARM INSTANCE]/dmp/projects/robust
    ```
    **note**: it could be the case that this endpoint is not (yet) available at your d:swarm instance
    
    
2. normal import

    ```
        curl -v -XPOST -H "Content-Type: application/json"  -d"@[FILE NAME].json" http://[HOSTNAME OR IP TO YOUR D:SWARM INSTANCE]/dmp/projects
    ```

**note**: please don't forget ro replace the variable parts (i.e. that one in '[]') with concrete things
