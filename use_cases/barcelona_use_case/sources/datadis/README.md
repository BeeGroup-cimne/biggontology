# Datadis consumption

The Datadis consumption dataset includes detailed information on hourly electricity consumption for each postal code. The data
is measured in kilowatt-hours (kWh) and is categorized by postal code, sector, and tariff.

## Gathering tool

This data source comes in the format of an CSV file where there are columns that contains consumptions for a postal
code.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so datadis -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The information is stored in a graph database called Neo4j, where all data is linked and harmonized according to the
BIGG ontology. Time series data will be stored in an Hbase table, with each endpoint providing different types of
information, each having its own row key.

#### Datadis Consumptions

````json
{
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes       | URI format                                                                           | Transformation actions |
|------------------------|--------------------------------------------------------------------------------------|------------------------|
| saref:Measurement      | namespace#Measurement-&lt;electricityDeviceId&gt;                                    |                        |
| bigg:Tariff            | namespaceTariff-&lt;tariff&gt;                                                       |                        |
| bigg:ContractedTariff  | namespace#ContractedTariff-&lt;tariff&gt                                             |                        |
| bigg:EnergySupplyPoint | namespace#EnergySupplyPoint-&lt;postalCode&gt;-&lt;economicSector&gt;-&lt;tariff&gt; |                        |
| saref:Device           | namespace#Device-&lt;postalCode&gt;-&lt;economicSector&gt;-&lt;tariff&gt;            |                        |

#### Object Properties=>

| Origin class           | Destination class                     | Relation                 |
|------------------------|---------------------------------------|--------------------------|
| gn:PostalCode          | saref:Measurement                     | saref:hasMeasurement     |
| saref:Measurement      | qudt:KiloW-HR-PER-M2                  | saref:isMeasuredIn       |
| saref:Measurement      | bigg:EnergyConsumptionGridElectricity | saref:relatesToProperty  |
| saref:Measurement      | bigg:&lt;economicSectorUri&gt;        | saref:relatesToProperty  |
| bigg:ContractedTariff  | bigg:Tariff                           | bigg:hasTariff           |
| bigg:EnergySupplyPoint | bigg:ContractedTariff                 | bigg:hasContractedTariff |
| saref:Device           | saref:Measurement                     | saref:makesMeasurement   |
| saref:Device           | bigg:EnergyConsumptionGridElectricity | saref:measuresProperty   |
| saref:Device           | bigg:EnergySupplyPoint                | s4syst:connectsAt        |

#### Data properties=>

| Ontology classes | Origin field | Harmonised field |
|------------------|--------------|------------------|
| bigg:Tariff      | tariff       | bigg:tariffName  |
| geosp:Geometry   | coordinates  | geosp:asGeoJSON  |



