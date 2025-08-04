# Gas consumtion weather description
The Digital Model Elevation Data contains the height above sea level for a 100-meter grid. With the help of a model, we obtain this data at the building level.

## Gathering tool
The data is automatically downloaded using a web scraper.

#### RUN import application
To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so emg -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format
The data imported will be stored in the Hbase table, each endpoint that provides a different kind of information will have its own  row key, that will be generated as follows:

#### EMG data
````json
{
    }
````



