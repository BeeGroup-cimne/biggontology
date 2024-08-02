# Neighbourhoods

The neighbourhoods file contains the neighbourhoods geometry information of barcelona city.

## Gathering tool

This data source comes in the format of an GPKG file.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so neighbourhoods -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The information is stored in a graph database called Neo4j, where all data is linked and harmonized according to the
BIGG ontology.

#### Neighbourhoods

````json
{
  "codi_districte": 1,
  "nom_districte": "Ciutat Vella",
  "codi_barri": 1,
  "nom_barri": "el Raval",
  "geometria_etrs89": "POLYGON ((430164.372950341 4581940.39758424, 430105.024480832 4581881.93614338,))"
}

````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes               | URI format                                        | Transformation actions |
|--------------------------------|---------------------------------------------------|------------------------|
| s4city:Neighbourhood           | namespace#Neighbourhood-&lt;codi_barri&gt;        |                        |
| gn:parentADM4, s4city:District | namespace#District-&lt;codi_districte&gt;         |                        |
| geosp:Geometry                 | namespace#NeighbourhoodPolygon-&lt;codi_barri&gt; |                        |

#### Relations=>

| Origin class                   | Destination class | Relation              |
|--------------------------------|-------------------|-----------------------|
| gn:parentADM4, s4city:District | geosp:Geometry    | bigg:hasNeighbourhood |
| s4city:Neighbourhood           | geosp:Geometry    | geosp:hasGeometry     |

#### Data properties=>

| Ontology classes     | Origin field | Harmonised field     |
|----------------------|--------------|----------------------|
| s4city:Neighbourhood | codi_barri   | bigg:neighbourhoodId |
| s4city:Neighbourhood | nom_barri    | gn:officialName      |
| geosp:Geometry       | coordinates  | geosp:asGeoJSON      |


