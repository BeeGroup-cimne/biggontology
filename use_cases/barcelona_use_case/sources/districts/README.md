# Districts

The districts file contains the district geometry information of barcelona city.

## Gathering tool

This data source comes in the format of an GeoJSON file.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so districts -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The information is stored in a graph database called Neo4j, where all data is linked and harmonized according to the
BIGG ontology.

#### Municipalities

````json
{
  "type": "Feature",
  "properties": {
    "CODIMUNI": "080193",
    "NOMMUNI": "Barcelona",
    "AREAOFI": null,
    "AREAPOL": 101.7629,
    "CODICOMAR": "13",
    "CODIPROV": "08",
    "VALIDDE": null,
    "DATAALTA": "202001011200"
  },
  "geometry": {
    "type": "MultiPolygon",
    "coordinates": [
      [
        [
          [
            2.178545014164631,
            41.37480008768268
          ],
          [
            2.17797105321016,
            41.37408466496421
          ]
        ]
      ]
    ]
  }
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes               | URI format                              | Transformation actions |
|--------------------------------|-----------------------------------------|------------------------|
| gn:parentADM4, s4city:District | namespace#District-&lt;DISTRICTE&gt;    |                        |
| gn:parentADM3                  | namespace#Municipality-&lt;MUNICIPI&gt; |                        |
| geosp:Geometry                 | namespace#Polygon-&lt;DISTRICTE&gt;     |                        |

#### Relations=>

| Origin class                   | Destination class                     | Relation                 |
|--------------------------------|---------------------------------------|--------------------------|
| gn:parentADM4, s4city:District | geosp:Geometry                        | geosp:hasGeometry        |
| gn:parentADM3                  | gn:parentADM4, s4city:District        | bigg:hasDivision         |

#### Data properties=>

| Ontology classes               | Origin field | Harmonised field |
|--------------------------------|--------------|------------------|
| gn:parentADM4, s4city:District | DISTRICTE    | bigg:districtId  |
| geosp:Geometry                 | coordinates  | geosp:asGeoJSON  |


