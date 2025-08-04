# Electricity consumtion Endesa

The Endesa consumption contains the monthly electricity consumption for each Address(postal code, street and number).

## Gathering tool

This data source comes in the format of an XLSX file where there are columns that contains consumptions for address.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so endesa -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The data imported will be stored in the Hbase table, each endpoint that provides a different kind of information will
have its own row key, that will be generated as follows:

#### Endesa data

````json
{
  "PROVINCE__C": 8,
  "PROVINCE_DESCRIPTION__C": "BARCELONA",
  "BOROUGH__C": 19,
  "BOROUGH_DESCRIPTION__C": "BARCELONA",
  "STREET_TYPE__C": "AV",
  "STREET_DESCRIPTION__C": "DIAGONAL",
  "STREET_NUMBER__C": 1,
  "Postal_Code__c": 8019,
  "NUM_CONTRATOS": 111,
  "CONSUMO_M1": 1783939.524,
  "CONSUMO_M2": 1620946.931,
  "CONSUMO_M3": 1800876.616,
  "CONSUMO_M4": 1732585.82,
  "CONSUMO_M5": 2172934.608,
  "CONSUMO_M6": 2462412.445,
  "CONSUMO_M7": 1726196.856,
  "CONSUMO_M8": 1768447.932,
  "CONSUMO_M9": 2443390.437,
  "CONSUMO_M10": 2237319.235,
  "CONSUMO_M11": 1969627.639,
  "CONSUMO_M12": 1931368.887
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes                      | URI format                                            | Transformation actions |
|---------------------------------------|-------------------------------------------------------|------------------------|
| s4bldg:Building                       | namespace#Building-&lt;reference&gt;                  |                        |
| s4agri:Deployment                     | namespace#Deployment-&lt;reference&gt;                |                        |
| s4syst:System, bigg:ElectricitySystem | namespace#System-Electricity-&lt;reference&gt;        |                        |
| saref:Device, bigg:ElectricityDevice  | namespace#Device-Electricity-Endesa-&lt;reference&gt; |                        |
| saref:Measurement                     | namespace#Measurement-&lt;endesaId&gt;                |                        |

#### Object Properties=>

| Origin class                          | Destination class                     | Relation                 |
|---------------------------------------|---------------------------------------|--------------------------|
| s4agri:Deployment                     | s4bldg:Building                       | s4agri:isDeployedAtSpace |
| s4agri:Deployment                     | s4syst:System, bigg:ElectricitySystem | ssn:hasDeployment        |
| s4syst:System, bigg:ElectricitySystem | saref:Device, bigg:ElectricityDevice  | s4syst:hasSubSystem      |
| saref:Device, bigg:ElectricityDevice  | saref:Measurement                     | saref:makesMeasurement   |
| saref:Device, bigg:ElectricityDevice  | bigg:EnergyConsumptionGridElectricity | saref:measuresProperty   |
| saref:Measurement                     | bigg:EnergyConsumptionGridElectricity | saref:relatesToProperty  |
| saref:Measurement                     | qudt:KiloW-HR                         | saref:isMeasuredIn       |

#### Data properties=>

| Ontology classes  | Origin field | Harmonised field |
|-------------------|--------------|------------------|
| saref:Measurement | endesaId     | bigg:hash        |