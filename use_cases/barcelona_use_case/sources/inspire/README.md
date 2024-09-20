# Inspire description

Inspire(Cadaster) is a data source containing points and polygons in geojson format.

## Gathering tool

This data source comes in the format of an GeoJSON file where there are two values for each building, first one have the
building centroid, the second one contain the polygon GeoJSON and all the information about the building.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so Inspire -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The data imported will be stored:

#### Buidings

````json
{
  "buildings": {
    "point": [
      {
        "type": "Feature",
        "properties": {
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
          "referenceGeometry": true,
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
          "area": 31.53759765625,
          "perimeter": 25.729075441229419
        },
        "geometry": {
          "type": "Point",
          "coordinates": "[ 438092.016499999852385, 4589396.840500000864267 ]"
        }
      }
    ],
    "geojson": [
      {
        "type": "Feature",
        "properties": {
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
          "referenceGeometry": true,
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
          "area": 31.53759765625,
          "perimeter": 25.729075441229419
        },
        "geometry": {
          "type": "Polygon",
          "coordinates": "[ [ [ 438087.647, 4589399.393000000156462 ], [ 438090.146, 4589401.542000000365078 ], [ 438096.386, 4589394.287999999709427 ], [ 438093.886999999987893, 4589392.139000000432134 ], [ 438087.647, 4589399.393000000156462 ] ] ]"
        }
      }
    ]
  }
}
````

#### BuildingSpace

````json
{
  "buildingsSpaces": {
    "punto": [
      {
        "type": "Feature",
        "properties": {
          "gml_id": "ES.SDGC.BU.000400400DF38H_part1",
          "beginLifespanVersion": "2007-04-23T00:00:00",
          "conditionOfConstruction": null,
          "localId": "000400400DF38H_part1",
          "namespace": "ES.SDGC.BU",
          "horizontalGeometryEstimatedAccuracy": 0.1,
          "horizontalGeometryEstimatedAccuracy_uom": "m",
          "horizontalGeometryReference": "footPrint",
          "referenceGeometry": true,
          "numberOfFloorsAboveGround": 1,
          "heightBelowGround": 0,
          "heightBelowGround_uom": "m",
          "numberOfFloorsBelowGround": 0,
          "area": 22.7852783203125,
          "perimeter": 20.111491819503449
        },
        "geometry": {
          "type": "Point",
          "coordinates": "[ 438086.824925219058059, 4589409.676963367499411 ]"
        }
      }
    ],
    "geojson": [
      {
        "type": "Feature",
        "properties": {
          "gml_id": "ES.SDGC.BU.000400400DF38H_part1",
          "beginLifespanVersion": "2007-04-23T00:00:00",
          "conditionOfConstruction": null,
          "localId": "000400400DF38H_part1",
          "namespace": "ES.SDGC.BU",
          "horizontalGeometryEstimatedAccuracy": 0.1,
          "horizontalGeometryEstimatedAccuracy_uom": "m",
          "horizontalGeometryReference": "footPrint",
          "referenceGeometry": true,
          "numberOfFloorsAboveGround": 1,
          "heightBelowGround": 0,
          "heightBelowGround_uom": "m",
          "numberOfFloorsBelowGround": 0,
          "area": 22.7852783203125,
          "perimeter": 20.111491819503449
        },
        "geometry": {
          "type": "Polygon",
          "coordinates": "[ [ [ 438087.672000000020489, 4589406.048000000417233 ], [ 438083.363499999977648, 4589411.057 ], [ 438085.977499999979045, 4589413.30599999986589 ], [ 438090.286499999987427, 4589408.29700000025332 ], [ 438087.672000000020489, 4589406.048000000417233 ] ] ]"
        }
      }
    ]
  }
}
````

#### Address

````json
{
  "address": {
    "punto": [
      {
        "type": "Feature",
        "properties": {
          "gml_id": "ES.SDGC.AD.08.015.1147.S-N.000400300DF38H",
          "localId": "08.015.1147.S-N.000400300DF38H",
          "namespace": "ES.SDGC.AD",
          "specification": "Parcel",
          "method": "fromFeature",
          "default": true,
          "designator": "S-N",
          "type": 1,
          "level": "siteLevel",
          "validFrom": null,
          "beginLifespanVersion": "2007-04-23T00:00:00"
        },
        "geometry": {
          "type": "Point",
          "coordinates": "[ 438092.01, 4589395.339999999850988 ]"
        }
      },
      {
        "type": "Feature",
        "properties": {
          "gml_id": "ES.SDGC.AD.08.015.1147.S-N.000400400DF38H",
          "localId": "08.015.1147.S-N.000400400DF38H",
          "namespace": "ES.SDGC.AD",
          "specification": "Parcel",
          "method": "fromFeature",
          "default": true,
          "designator": "S-N",
          "type": 1,
          "level": "siteLevel",
          "validFrom": null,
          "beginLifespanVersion": "2007-04-23T00:00:00"
        },
        "geometry": {
          "type": "Point",
          "coordinates": "[ 438093.88, 4589399.78000000026077 ]"
        }
      }
    ]
  }
}

````

## Harmonization

The harmonization of the data will be done with the following mapping:

### Building=>

#### Classes=>

| Ontology classes     | URI format                                                                  | Transformation actions |
|----------------------|-----------------------------------------------------------------------------|------------------------|
| s4bldg:Building      | namespace#Building-&lt;building_gml_id&gt;                                  |                        |
| gn:PostalCode        | namespace#PostalCodes-&lt;CODPOS&gt;                                        |                        |
| gn:parentADM5        | namespace#CensusTract-&lt;MUNDISSEC&gt;                                     |                        |
| s4city:Neighbourhood | namespace#Neighbourhood-&lt;codi_barri&gt;                                  |                        |
| geo:Point            | namespace#Point-&lt;properties.building_gml_id&gt;                          |                        |
| geosp:Geometry       | namespace#Polygon-&lt;properties.building_gml_id&gt;                        |                        |
| saref:Measurement    | namespace#Measurement-&lt;building_gml_id&gt;-&lt;officialAreaReference&gt; |                        |
| saref:Measurement    | namespace#Measurement-&lt;building_gml_id&gt;-&lt;BuiltUpLandArea&gt;       |                        |
| saref:UnitOfMeasure  | qudt:M2                                                                     |                        |
| saref:Property       | bigg#GrossFloorArea                                                         |                        |
| saref:Property       | bigg#BuiltUpLandArea                                                        |                        |

#### Object Properties=>

| Origin class         | Destination class    | Relation                |
|----------------------|----------------------|-------------------------|
| s4bldg:Building      | saref:Measurement    | geosp:hasArea           |
| s4bldg:Building      | saref:Measurement    | geosp:hasArea           |
| s4bldg:Building      | geo:Point            | geosp:hasGeometry       |
| s4bldg:Building      | geosp:Geometry       | geosp:hasGeometry       |
| gn:PostalCode        | s4bldg:Building      | geosp:sfContains        |
| gn:parentADM5        | s4bldg:Building      | geosp:sfContains        |
| s4city:Neighbourhood | s4bldg:Building      | geosp:sfContains        |
| saref:Measurement    | qudt:M2              | saref:isMeasuredIn      |
| saref:Measurement    | bigg:GrossFloorArea  | saref:relatesToProperty |
| saref:Measurement    | qudt:M2              | saref:isMeasuredIn      |
| saref:Measurement    | bigg:BuiltUpLandArea | saref:relatesToProperty |

#### Data properties=>

| Ontology classes  | Origin field            | Harmonised field         |
|-------------------|-------------------------|--------------------------|
| s4bldg:Building   | beginLifespanVersion    | bigg:startState          |
| s4bldg:Building   | conditionOfConstruction | bigg:state               |
| s4bldg:Building   | beginning               | bigg:startConstruction   |
| s4bldg:Building   | end                     | bigg:endConstruction     |
| s4bldg:Building   | endLifespanVersion      | bigg:endState            |
| s4bldg:Building   | informationSystem       | bigg:cadasterDetailedUrl |
| s4bldg:Building   | reference               | bigg:cadastralId         |
| s4bldg:Building   | currentUse              | bigg:mainUse             |
| s4bldg:Building   | numberOfBuildingUnits   | bigg:buildingUnits       |
| s4bldg:Building   | numberOfDwellings       | bigg:dwellings           |
| geo:Point         | geometry.coordinates    | geosp:asGeoJSON          |
| geosp:Geometry    | geometry.coordinates    | geosp:asGeoJSON          |
| saref:Measurement | value                   | saref:hasValue           |
| saref:Measurement | area                    | saref:hasValue           |

### BuildingSpace=>

#### Classes=>

| Ontology classes          | URI format                                                    | Transformation actions |
|---------------------------|---------------------------------------------------------------|------------------------|
| s4bldg:Building           | namespace#Building-&lt;building_gml_id&gt;                    |                        |
| bigg:InspireBuildingSpace | namespace#InspireBuildingSpace-&lt;localId&gt;                |                        |
| geo:Point                 | namespace#Point-&lt;properties.localId&gt;                    |                        |
| geosp:Geometry            | namespace#Neighbourhood-&lt;codi_barri&gt;                    |                        |
| geo:Point                 | namespace#Point-&lt;properties.localId&gt;                    |                        |
| geosp:Geometry            | namespace#Polygon-&lt;properties.localId&gt;                  |                        |
| saref:Measurement         | namespace#Measurement-&lt;localId&gt;-&lt;BuiltUpLandArea&gt; |                        |
| saref:UnitOfMeasure       | qudt:M2                                                       |                        |
| saref:Property            | bigg#BuiltUpLandArea                                          |                        |

#### Object Properties=>

| Origin class              | Destination class         | Relation                |
|---------------------------|---------------------------|-------------------------|
| s4bldg:Building           | bigg:InspireBuildingSpace | s4bldg:hasSpace         |
| bigg:InspireBuildingSpace | saref:Measurement         | geosp:hasArea           |
| bigg:InspireBuildingSpace | geo:Point                 | geosp:hasGeometry       |
| bigg:InspireBuildingSpace | geosp:Geometry            | geosp:hasGeometry       |
| saref:Measurement         | qudt:M2                   | saref:isMeasuredIn      |
| saref:Measurement         | bigg:BuiltUpLandArea      | saref:relatesToProperty |

#### Data properties=>

| Ontology classes          | Origin field              | Harmonised field               |
|---------------------------|---------------------------|--------------------------------|
| bigg:InspireBuildingSpace | localId                   | bigg:cadastralLocalId          |
| bigg:InspireBuildingSpace | numberOfFloorsAboveGround | bigg:numberOfFloorsAboveGround |
| bigg:InspireBuildingSpace | numberOfFloorsBelowGround | bigg:numberOfFloorsBelowGround |
| geo:Point                 | geometry.coordinates      | geosp:asGeoJSON                |
| geosp:Geometry            | geometry.coordinates      | geosp:asGeoJSON                |
| saref:Measurement         | area                      | saref:hasValue                 |

### Address=>

#### Classes=>

| Ontology classes | URI format                                 | Transformation actions |
|------------------|--------------------------------------------|------------------------|
| s4bldg:Building  | namespace#Building-&lt;building_gml_id&gt; |                        |
| vcard:Address    | namespace#Address-&lt;building_gml_id&gt;  |                        |
| geo:Point        | namespace#Point-&lt;properties.localId&gt; |                        |

#### Object Properties=>

| Origin class    | Destination class | Relation         |
|-----------------|-------------------|------------------|
| s4bldg:Building | vcard:Address     | vcard:hasAddress |
| vcard:Address   | geo:Point         | vcard:hasGeo     |

#### Data properties=>

| Ontology classes | Origin field         | Harmonised field   |
|------------------|----------------------|--------------------|
| vcard:Address    | building_gml_id      | bigg:addressId     |
| vcard:Address    | specification        | bigg:specification |
| vcard:Address    | designator           | bigg:streetNumber  |
| vcard:Address    | street_name          | bigg:streetName    |
| vcard:Address    | beginLifespanVersion | bigg:startState    |
| geo:Point        | geometry.coordinates | geosp:asGeoJSON    |

