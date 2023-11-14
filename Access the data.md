# Access the data

Sharedmobility.ch aggregates the data of shared mobility providers in near real-time. The data is available as:

* [GBFS 2.3 endpoint](https://github.com/SFOE/sharedmobility/blob/main/Access%20the%20data.md#gbfs-20-endpoint)
* [GBFS 2.0 endpoint](https://github.com/SFOE/sharedmobility/blob/main/Access%20the%20data.md#gbfs-20-endpoint)
* [Web-Service](https://github.com/SFOE/sharedmobility/blob/main/Access%20the%20data.md#web-service)

**Terms of use**: Open use. Must provide the source.

* You may use this dataset for non-commercial purposes.
* You may use this dataset for commercial purposes.
* You must provide the source (author, title and link to the dataset).

See [opendata.swiss](https://opendata.swiss/en/dataset/standorte-und-verfugbarkeit-von-shared-mobility-angeboten) for more information.


## GBFS 2.3 endpoint

GBFS 2.3 endpoint:
[sharedmobility.ch/v2](https://sharedmobility.ch/v2/)

:warning: **Please note that a valid email is required in the Authorization header as followed:**
```
curl -H "Authorization: gbfs@sharedmobility.ch" -i "https://sharedmobility.ch/v2/"
```

## GBFS 2.0 endpoint

GBFS 2.0 endpoint:
[sharedmobility.ch/gbfs.json](https://sharedmobility.ch/gbfs.json)

Please check the differences to GBFS 2.0 made to support multiple systems in one feed:

[Additions to GBFS](https://github.com/SFOE/sharedmobility/blob/main/Additions%20to%20GBFS.md)

## Web-Service

See [Access sharedmobility.ch data using the REST API](https://github.com/SFOE/sharedmobility/blob/main/Sharedmobility.ch-API.md)

## Service status

See [Service status](https://stats.uptimerobot.com/xx6M9cLVN3) for uptime information.
