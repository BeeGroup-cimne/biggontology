# Vegetation index NDVI description

The NDVI represents the normalised difference vegetation index, with a resolution of 1m.

## Gathering tool

This data source is presented in tif format, this data is crossed with a buffer of the cadastre building footprints to
obtain a histogram of the raster data.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so ndvi -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The data imported will be stored in the Hbase table, each endpoint that provides a different kind of information will
have its own row key, that will be generated as follows:

#### NDVI data

````json
{
  "fid": 1,
  "gml_id": "ES.SDGC.BU.000400300DF38H",
  "beginLifespanVersion": "2007-04-23T00:00:00",
  "conditionOfConstruction": "functional",
  "beginning": "1933-01-01T00:00:00",
  "end": "1933-01-01T00:00:00",
  "endLifespanVersion": null,
  "informationSystem": "https://www1.sedecatastro.gob.es/CYCBienInmueble/OVCListaBienes.aspx?rc1=0004003&rc2=00DF38H",
  "reference": "000400300DF38H",
  "localId": "000400300DF38H",
  "namespace": "ES.SDGC.BU",
  "horizontalGeometryEstimatedAccuracy": 0.1,
  "horizontalGeometryEstimatedAccuracy_uom": "m",
  "horizontalGeometryReference": "footPrint",
  "referenceGeometry": "verdadero",
  "currentUse": null,
  "numberOfBuildingUnits": 1,
  "numberOfDwellings": 1,
  "numberOfFloorsAboveGround": null,
  "documentLink": "http://ovc.catastro.meh.es/OVCServWeb/OVCWcfLibres/OVCFotoFachada.svc/RecuperarFotoFachadaGet?ReferenciaCatastral=000400300DF38H",
  "format": "jpeg",
  "sourceStatus": "NotOfficial",
  "officialAreaReference": "grossFloorArea",
  "value": 40,
  "value_uom": "m2",
  "HISTO_-0.02": 0,
  "HISTO_-0.01": 0,
  "HISTO_0": 0,
  "HISTO_0.01": 0,
  "HISTO_0.02": 0,
  "HISTO_0.03": 0,
  "HISTO_0.04": 2,
  "HISTO_0.05": 3,
  "HISTO_0.06": 8,
  "HISTO_0.07": 17,
  "HISTO_0.08": 56,
  "HISTO_0.09": 106,
  "HISTO_0.1": 43,
  "HISTO_0.11": 16,
  "HISTO_0.12": 23,
  "HISTO_0.13": 22,
  "HISTO_0.14": 20,
  "HISTO_0.15": 30,
  "HISTO_0.16": 11,
  "HISTO_0.17": 14,
  "HISTO_0.18": 5,
  "HISTO_0.19": 7,
  "HISTO_0.2": 12,
  "HISTO_0.21": 11,
  "HISTO_0.22": 3,
  "HISTO_0.23": 4,
  "HISTO_0.24": 5,
  "HISTO_0.25": 10,
  "HISTO_0.26": 5,
  "HISTO_0.27": 6,
  "HISTO_0.28": 5,
  "HISTO_0.29": 6,
  "HISTO_0.3": 6,
  "HISTO_0.31": 3,
  "HISTO_0.32": 7,
  "HISTO_0.33": 7,
  "HISTO_0.34": 7,
  "HISTO_0.35": 7,
  "HISTO_0.36": 10,
  "HISTO_0.37": 6,
  "HISTO_0.38": 6,
  "HISTO_0.39": 5,
  "HISTO_0.4": 6,
  "HISTO_0.41": 5,
  "HISTO_0.42": 10,
  "HISTO_0.43": 11,
  "HISTO_0.44": 9,
  "HISTO_0.45": 4,
  "HISTO_0.46": 4,
  "HISTO_0.47": 9,
  "HISTO_0.48": 5,
  "HISTO_0.49": 1,
  "HISTO_0.5": 3,
  "HISTO_0.51": 6,
  "HISTO_0.52": 0,
  "HISTO_0.53": 1,
  "HISTO_0.54": 5,
  "HISTO_0.55": 1,
  "HISTO_0.56": 1,
  "HISTO_0.57": 0,
  "HISTO_0.59": 1,
  "HISTO_0.61": 0,
  "HISTO_0.74": 0
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes               | URI format                              | Transformation actions |
|--------------------------------|-----------------------------------------|------------------------|
| s4bldg:Building                | namespace#Building-&lt;reference&gt;    |                        |
| s4agri:Deployment              | namespace#Deployment-&lt;reference&gt;  |                        |
| s4syst:System, bigg:NdviSystem | namespace#System-NDVI-&lt;reference&gt; |                        |
| saref:Device, bigg:NdviDevice  | namespace#Device-NDVI-&lt;reference&gt; |                        |
| saref:Measurement              | namespace#Measurement-&lt;ndviId&gt;    |                        |
| bigg:Ndvi                      | bigg:Ndvi                               |                        |
| qudt:PERCENT                   | qudt:PERCENT                            |                        |

#### Object Properties=>

| Origin class                   | Destination class              | Relation                 |
|--------------------------------|--------------------------------|--------------------------|
| s4agri:Deployment              | s4bldg:Building                | s4agri:isDeployedAtSpace |
| s4agri:Deployment              | s4syst:System, bigg:NdviSystem | ssn:hasDeployment        |
| s4syst:System, bigg:NdviSystem | saref:Device, bigg:NdviDevice  | s4syst:hasSubSystem      |
| saref:Device, bigg:NdviDevice  | saref:Measurement              | saref:makesMeasurement   |
| saref:Device, bigg:NdviDevice  | bigg:Ndvi                      | saref:measuresProperty   |
| saref:Measurement              | bigg:Ndvi                      | saref:relatesToProperty  |
| saref:Measurement              | qudt:PERCENT                   | saref:isMeasuredIn       |

#### Data properties=>

| Ontology classes  | Origin field | Harmonised field |
|-------------------|--------------|------------------|
| saref:Measurement | ndviId       | bigg:hash        |




