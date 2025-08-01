# Electricity consumption

The electricity consumption dataset includes detailed information on 15-minute intervals of electricity consumption for
each postal code. The data is measured in kilowatt-hours (kWh) and is categorized by postal code (RTA) and sector.

## Gathering tool

This data source comes in the format of an CSV file where there are columns that contains consumptions for a postal
code.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so electricity -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The information is stored in a graph database called Neo4j, where all data is linked and harmonized according to the
BIGG ontology. Time series data will be stored in an Hbase table, with each endpoint providing different types of
information, each having its own row key.

#### Electricity Consumptions

````json
{
  "CP3": "H1K",
  "Secteur": "COM",
  "DateInterval": "2021-01-01T00:00:00.000Z",
  "kWh": "592.5",
  "kWh_Moyen": "2.65",
  "kWh_std": "6.39",
  "pctIntervals": "0.987",
  "nbClients": "227"
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes                      | URI format                                         | Transformation actions |
|---------------------------------------|----------------------------------------------------|------------------------|
| s4agri:Deployment                     | namespace#Deployment-&lt;CP3&gt;                   |                        |
| s4syst:System, bigg:ElectricitySystem | namespace#System-RTA-Electricity-&lt;id&gt;        |                        |
| saref:Device, bigg:ElectricityDevice  | namespace#Device-RTA-Electricity-&lt;id&gt;        |                        |
| saref:Measurement                     | namespace#Tariff-Measurement-&lt;electricityId&gt; |                        |

#### Object Properties=>

| Origin class                          | Destination class                     | Relation                 |
|---------------------------------------|---------------------------------------|--------------------------|
| s4agri:Deployment                     | gn:parentADM4                         | s4agri:isDeployedAtSpace |
| s4agri:Deployment                     | s4syst:System, bigg:ElectricitySystem | ssn:hasDeployment        |
| s4syst:System, bigg:ElectricitySystem | saref:Device, bigg:ElectricityDevice  | s4syst:hasSubSystem      |
| saref:Device, bigg:ElectricityDevice  | saref:Measurement                     | saref:makesMeasurement   |
| saref:Device, bigg:ElectricityDevice  | bigg:EnergyConsumptionGridElectricity | saref:measuresProperty   |
| saref:Device, bigg:ElectricityDevice  | bigg:&lt;Secteur&gt;SectorElectricity | saref:measuresProperty   |
| saref:Measurement                     | bigg:EnergyConsumptionGridElectricity | saref:relatesToProperty  |
| saref:Measurement                     | bigg:&lt;Secteur&gt;SectorElectricity | saref:relatesToProperty  |
| saref:Measurement                     | qudt:KiloW-HR                         | saref:isMeasuredIn       |

#### Data properties=>

| Ontology classes  | Origin field  | Harmonised field |
|-------------------|---------------|------------------|
| saref:Measurement | electricityId | bigg:hash        |






