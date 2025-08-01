# Gas consumption

The gas consumption dataset includes detailed information on monthly gas consumption for
each postal code. The data is measured in cubic meter (m3) and is categorized by postal code (RTA) and sector.

## Gathering tool

This data source comes in the format of an XLSX file where there are columns that contains consumptions for a postal
code.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so gas -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The information is stored in a graph database called Neo4j, where all data is linked and harmonized according to the
BIGG ontology. Time series data will be stored in an Hbase table, with each endpoint providing different types of
information, each having its own row key.

#### Gas Consumptions

````json
{
  "RTA": "H1K",
  "Type chauffage": "Individuel",
  "Nombre de clients \\u00c9": "452",
  "month": "2019-01",
  "value": "331.6858407079646"
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes              | URI format                                 | Transformation actions |
|-------------------------------|--------------------------------------------|------------------------|
| s4agri:Deployment             | namespace#Deployment-&lt;RTA&gt;           |                        |
| s4syst:System, bigg:GasSystem | namespace#System-RTA-Gas-&lt;id&gt;        |                        |
| saref:Device, bigg:GasDevice  | namespace#Device-RTA-Gas-&lt;id&gt;        |                        |
| saref:Measurement             | namespace#Tariff-Measurement-&lt;gasId&gt; |                        |

#### Object Properties=>

| Origin class                  | Destination class             | Relation                 |
|-------------------------------|-------------------------------|--------------------------|
| s4agri:Deployment             | gn:parentADM4                 | s4agri:isDeployedAtSpace |
| s4agri:Deployment             | s4syst:System, bigg:GasSystem | ssn:hasDeployment        |
| s4syst:System, bigg:GasSystem | saref:Device, bigg:GasDevice  | s4syst:hasSubSystem      |
| saref:Device, bigg:GasDevice  | saref:Measurement             | saref:makesMeasurement   |
| saref:Device, bigg:GasDevice  | bigg:EnergyConsumptionGas     | saref:measuresProperty   |
| saref:Measurement             | bigg:EnergyConsumptionGas     | saref:relatesToProperty  |
| saref:Measurement             | qudt:M3                       | saref:isMeasuredIn       |

#### Data properties=>

| Ontology classes  | Origin field | Harmonised field |
|-------------------|--------------|------------------|
| saref:Measurement | gasId        | bigg:hash        |









