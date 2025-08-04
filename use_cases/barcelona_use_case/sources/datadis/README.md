# Datadis consumption

The Datadis consumption dataset includes detailed information on hourly electricity consumption for each postal code.
The data is measured in kilowatt-hours (kWh) and is categorized by postal code, sector, and tariff.

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
  "dataDay": "1",
  "dataMonth": "7",
  "dataYear": "2023",
  "community": "Catalu\\u00f1a",
  "province": "Barcelona",
  "municipality": "BARCELONA",
  "postalCode": "08015",
  "fare": ">= 1 kV Y < 30 kV",
  "timeDiscrimination": "GENERAL ALTA TENSI\\u00d3N",
  "measurePointType": null,
  "sumEnergy": "98473",
  "sumContracts": "11",
  "tension": "E2",
  "economicSector": "SERVICIOS",
  "distributor": null,
  "mi1": "4317",
  "mi2": "3912",
  "mi3": "2850",
  "mi4": "1544",
  "mi5": "1950",
  "mi6": "3462",
  "mi7": "3627",
  "mi8": "4047",
  "mi9": "4267",
  "mi10": "4510",
  "mi11": "4404",
  "mi12": "4426",
  "mi13": "4682",
  "mi14": "4698",
  "mi15": "4812",
  "mi16": "4884",
  "mi17": "4777",
  "mi18": "4936",
  "mi19": "4770",
  "mi20": "4911",
  "mi21": "5004",
  "mi22": "4166",
  "mi23": "3788",
  "mi24": "3729",
  "mi25": "0"
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](harmonizer/mapping.yaml):

#### Classes=>

| Ontology classes       | URI format                                                                           | Transformation actions |
|------------------------|--------------------------------------------------------------------------------------|------------------------|
| gn:PostalCode          | namespace#PostalCodes-&lt;postalCode&gt;                                             |                        |
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
