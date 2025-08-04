# HUTS description

This data contains a description, categorization and geolocation of each tourist establishment.

## Gathering tool

This data source comes in the format of an CSV file.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so HUTS -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The data imported will be stored:

#### Buidings

````json
{
  "Adreca ": "Carrer Punta Falconera, n\u00fam. 62",
  "CIF": "A17214024",
  "Capacitat total unitats acampada": 870,
  "Categoria": "3 estrelles",
  "Codi Postal ": 17480,
  "Comarca ": "Alt Empord\u00e0",
  "D\u00edgit control": 30,
  "Estat": "Alta",
  "Marca tur\u00edstica": "Costa Brava",
  "Municipi ": "Roses",
  "Nom del titular ": NaN,
  "N\u00famero d'inscripci\u00f3": "KG-000092",
  "Primer Cognom ": NaN,
  "Ra\u00f3 Social ": "RODASMAR, SA",
  "R\u00e8tol ": "Rodas",
  "SSTT": "Girona",
  "Segon Cognom ": NaN,
  "Total unitats acampada": 290,
  "_id": "622efcb9c2332f54f7ab7095",
  "address_x": "Punta Falconera 62",
  "matches": "DE LA PUNTA FALCONERA 62",
  "xcoord": 3.15309771294596,
  "ycoord": 42.2684944362531
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes          | URI format                                                                  | Transformation actions |
|---------------------------|-----------------------------------------------------------------------------|------------------------|
| s4bldg:Building           | namespace#Building-&lt;reference&gt;                                        |                        |
| bigg:TouristBuildingSpace | namespace#TouristBuildingSpace-&lt;huts_type&gt-&lt;Número d'inscripció&gt; |                        |

#### Object Properties=>

| Origin class    | Destination class         | Relation        |
|-----------------|---------------------------|-----------------|
| s4bldg:Building | bigg:TouristBuildingSpace | s4bldg:hasSpace |

#### Data properties=>

| Ontology classes          | Origin field | Harmonised field |
|---------------------------|--------------|------------------|
| bigg:TouristBuildingSpace | Categoria    | bigg:Category    |
| bigg:TouristBuildingSpace | Total places | bigg:Capacity    |
| bigg:TouristBuildingSpace | Estat        | bigg:State       |




