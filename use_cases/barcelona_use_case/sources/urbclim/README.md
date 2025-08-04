# Urbclim weather description

The UrbClim project is an urban climate model developed
by [VITO](https://vito.be/en/applications/urbclim-limit-climate-risks-your-city) to simulate and analyse the climate in
urban areas at the agglomeration scale, with a spatial resolution of a few hundred metres.

## Gathering tool

This data source comes in weather file format. We process these climate files to obtain the air temperature and relative
humidity.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so urbclim -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The data imported will be stored in the Hbase table, each endpoint that provides a different kind of information will
have its own row key, that will be generated as follows:

#### UrbClim data

````json
{
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](mapping.yaml):

#### Classes=>

| Ontology classes      | URI format                                                         | Transformation actions |
|-----------------------|--------------------------------------------------------------------|------------------------|
| saref:Device          | namespace#Device-AirTemperature-&lt;latitude&gt;-&lt;longitude&gt; |                        |
| s4agri:WeatherStation | namespace#System-WeatherStation-&lt;latitude&gt;-&lt;longitude&gt; |                        |
| saref:Measurement     | namespace#&lt;weatherId&gt;                                        |                        |
| saref:UnitOfMeasure   | namespace#unit-K                                                   |                        |
| saref:Property        | namespace#Property&lt;DryBulbTemperature&gt;                       |                        |

#### Object Properties=>

| Origin class          | Destination class   | Relation                |
|-----------------------|---------------------|-------------------------|
| saref:Measurement     | saref:UnitOfMeasure | saref:isMeasuredIn      |
| s4agri:WeatherStation | saref:Device        | s4syst:hasSubSystem     |
| saref:Measurement     | saref:Property      | saref:relatesToProperty |
| saref:Device          | saref:Measurement   | saref:makesMeasurement  |



