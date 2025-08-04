# Census Tracts

The censusTracts file contains the census tracts, district geometry information of barcelona city.

## Gathering tool

This data source comes in the format of an GPKG file.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so census_tracts -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The information is stored in a graph database called Neo4j, where all data is linked and harmonized according to the
BIGG ontology.

#### Census Tracts

````json
{
  "type": "Feature",
  "properties": {
    "fid": 1,
    "MUNICIPI": "080193",
    "DISTRICTE": "01",
    "SECCIO": "001",
    "MUNDISSEC": "08019301001"
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

| Ontology classes               | URI format                                  | Transformation actions |
|--------------------------------|---------------------------------------------|------------------------|
| gn:parentADM5                  | namespace#CensusTract-&lt;censusTractId&gt; |                        |
| gn:parentADM4, s4city:District | namespace#District-&lt;districtId&gt;       |                        |
| geosp:Geometry                 | namespace#Polygon-&lt;censusTractId&gt;     |                        |

#### Object Properties=>

| Origin class                   | Destination class | Relation          |
|--------------------------------|-------------------|-------------------|
| gn:parentADM5                  | geosp:Geometry    | geosp:hasGeometry |
| gn:parentADM4, s4city:District | gn:parentADM5     | bigg:hasDivision  |

#### Data properties=>

| Ontology classes | Origin field   | Harmonised field   |
|------------------|----------------|--------------------|
| gn:parentADM5    | SECCIO: String | bigg:censusTractId |
| geosp:Geometry   | coordinates    | geosp:asGeoJSON    |