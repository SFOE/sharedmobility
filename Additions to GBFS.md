# Additions to GBFS

Sharedmobility.ch is based on the [General Bikeshare Feed Specification (GBFS)](https://github.com/NABSA/gbfs/blob/v2.0/gbfs.md) Version 2.0.
GBFS is optimized to represent one single system. In order to represent multiple systems in one feed, the following additions to GBFS V2.0 were made:

## Add providers.json

[Providers.json](https://bfe-test.oevfahrplan.ch/providers.json) (Link anpassen) was added as an additional JSON-File to the GBFS-Feed. Providers.json describes metainformation of every system. Fields are identical to system_informatin.json. One additional field (provider_id) was added (see also [List of shared mobility providers](https://github.com/SFOE/sharedmobility/blob/main/List%20of%20shared%20mobility%20providers.md).

## Changes in station_information.json

* The field station_id comprises the merged fields provider_id and station_id
* provider_id is added to stations as followed:
 ```json
{
  "last_updated" : 1605098383,
  "ttl" : 60,
  "version" : "2.0",
  "data" : {
    "stations" : [ {
      "station_id" : "carvelo2go:e4d4f78a-861d-49a9-c216-be6e288dec5a",
      "name" : "8610 im Stadtpark ",
      "lat" : 47.34867,
      "lon" : 8.71413,
      "address" : "Landihalle",
      "region_id" : "carvelo2go:936ccc56-80e6-441f-959b-da5747118c61",
      "post_code" : "8610",
      "provider_id" : "carvelo2go"
    }
```

## Changes in station_status.json

* The field station_id comprises themerged fields provider_id and station_id
* provider_id is added to stations as followed:
 ```json
{
  "last_updated" : 1605098165,
  "ttl" : 60,
  "version" : "2.0",
  "data" : {
    "stations" : [ {
      "station_id" : "donkey_thun:17447",
      "num_bikes_available" : 0,
      "num_docks_available" : 25,
      "last_reported" : 1605096513,
      "provider_id" : "donkey_thun"
    }
```

## Changes in free_bike_status.json

* The field bike_id comprises the merged fields provider_id and bike_id
* provider_id is added to bikes as followed:
 ```json
{
  "last_updated" : 1605099018,
  "ttl" : 60,
  "version" : "2.0",
  "data" : {
    "bikes" : [ {
      "bike_id" : "airbie-6759c:IszKSTulW6rLO0cJ",
      "lat" : 47.17566,
      "lon" : 8.515347,
      "is_disabled" : 0,
      "is_reserved" : 0,
      "provider_id" : "airbie-6759c"
    }
```


## Differences
* According to GBFS V2 the field bike_id in free_bike_status.json has to be rotated to a random string, at a minimum, after each trip to protect privacy. This is not fully supported by all providers.
