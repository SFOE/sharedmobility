# Additions to GBFS

Sharedmobility.ch is based on the [General Bikeshare Feed Specification (GBFS)](https://github.com/SFOE/sharedmobility/blob/main/Access%20the%20data.md) Version 2.0.
GBFS is optimized to represent one single system. In order to represent multiple systems in one feed, the following additions to GBFS V2.0 were made:

## Add providers.json

[Providers.json](https://bfe-test.oevfahrplan.ch/providers.json) (Link anpassen) was added as an additional JSON-File to the GBFS-Feed. Providers.json describes metainformation of every system. Fields are identical to system_informatin.json. One additional field (provider_id) was added (see also [List of shared mobility providers](https://github.com/SFOE/sharedmobility/blob/main/List%20of%20shared%20mobility%20providers.md).

## Changes in station_information.json

* The field station_id is connected from provider_id and station_id
* provider_id is added to stations as followed:
 ```json
      "station_id" : "carvelo2go:1f20dbbd-a186-4ae4-ae0b-0236e4770a0f",
      "name" : "Agentur UMSICHT",
      "lat" : 47.04885,
      "lon" : 8.300365,
      "address" : "Klosterstrasse 21 a",
      "region_id" : "carvelo2go:404c3386-19d5-4931-b999-4f90fa9c9184",
      "post_code" : "6003",
      "provider_id" : "carvelo2go"
```





## Differences
* According to GBFS V2 the field bike_id in free_bike_status.json has to be rotated to a random string, at a minimum, after each trip to protect privacy. This is not fully supported by all providers.
