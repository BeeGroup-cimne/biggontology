# AEB consumption

The Barcelona Energy Agency (AEB) consumption dataset provides detailed electricity and gas yearly consumption data
categorized by census tract. The available years for gas consumption data are 2018, 2019, 2020, 2021, and 2022. The
available years for electricity consumption data are 2020, 2021, and 2022. In both cases, the unit of measurement is
kWh/CUPS.

## Gathering tool

The AEB (Annual Energy Balance) consumption data is provided in an XLSX file format.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so AEB_consumption -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The data imported will be stored in the Hbase table, each endpoint that provides a different kind of information will
have its own row key, that will be generated as follows:

#### AEB Consumptions

````json
{
}
````

## Harmonization

The harmonization of the data will be done with the following mapping:

#### Consumption=>

| Origin | Harmonization |
|--------|---------------|
|        |               | 



