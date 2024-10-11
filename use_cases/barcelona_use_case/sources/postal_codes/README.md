# Postal Codes

The Postal Codes file contains geometry information of barcelona city.

## Gathering tool

This data source comes in the format of an GPKG file.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so postal_codes_bcn -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The data imported will be stored in the Hbase table, each endpoint that provides a different kind of information will
have its own row key, that will be generated as follows:

#### Postal Codes

````json
{
  "PROV": "08",
  "CODPOS": "08041"
}
````

## Harmonization

The harmonization of the data will be done with the following mapping:

#### Postal Codes=>

| Origin | Harmonization              |
|--------|----------------------------|
| CODPOS | gn:PostalCode:postalCodeId | 



