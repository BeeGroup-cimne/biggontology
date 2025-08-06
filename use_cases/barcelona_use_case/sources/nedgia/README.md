# Gas consumption description

The Nedgia consumption contains the gas consumption for each Address(postal code, street and number).

## Gathering tool

This data source comes in the format of an XLSX file where there are columns that contains consumptions for address.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so nedgia -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The data imported will be stored in the Hbase table, each endpoint that provides a different kind of information will
have its own row key, that will be generated as follows:

#### Gas data

````json
{
  "cp": 8037,
  "municipio": "BARCELONA",
  "direccion": "MALLORCA0277",
  "consum_acum_2023": 30477.0,
  "N\\u00fam. CUPS": 9
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes              | URI format                             | Transformation actions |
|-------------------------------|----------------------------------------|------------------------|
| s4bldg:Building               | namespace#Building-&lt;reference&gt;   |                        |
| s4agri:Deployment             | namespace#Deployment-&lt;reference&gt; |                        |
| s4syst:System, bigg:GasSystem | namespace#System-Gas-&lt;reference&gt; |                        |
| saref:Device, bigg:GasDevice  | namespace#Device-Gas-&lt;reference&gt; |                        |
| saref:Measurement             | namespace#Measurement-&lt;gasId&gt;    |                        |

#### Object Properties=>

| Origin class                  | Destination class             | Relation                 |
|-------------------------------|-------------------------------|--------------------------|
| s4agri:Deployment             | s4bldg:Building               | s4agri:isDeployedAtSpace |
| s4agri:Deployment             | s4syst:System, bigg:GasSystem | ssn:hasDeployment        |
| s4syst:System, bigg:GasSystem | saref:Device, bigg:GasDevice  | s4syst:hasSubSystem      |
| saref:Device, bigg:GasDevice  | saref:Measurement             | saref:makesMeasurement   |
| saref:Device, bigg:GasDevice  | bigg:EnergyConsumptionGas     | saref:measuresProperty   |
| saref:Measurement             | bigg:EnergyConsumptionGas     | saref:relatesToProperty  |
| saref:Measurement             | qudt:KiloW-HR                 | saref:isMeasuredIn       |

#### Data properties=>

| Ontology classes  | Origin field | Harmonised field |
|-------------------|--------------|------------------|
| saref:Measurement | gasId        | bigg:hash        |



