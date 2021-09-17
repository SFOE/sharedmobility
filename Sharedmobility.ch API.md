# Access sharedmobility.ch data using the REST API
The data of the GBFS-endpoint of sharedmobility.ch can be accessed with a RESTful API. 
Here we show you some examples how to query the API.

## General information
* Swagger documentation: [api.sharedmobility.ch](https://api.sharedmobility.ch)

## Available endpoints
* [GET attributes](https://github.com/nrohrbach/sharedmobility/blob/main/Sharedmobility.ch%20API.md#get-attributes)
* [GET find](https://github.com/nrohrbach/sharedmobility/blob/main/Sharedmobility.ch%20API.md#get-find)
* [GET identify](https://github.com/nrohrbach/sharedmobility/blob/main/Sharedmobility.ch%20API.md#get-identify)
* [GET providers](https://github.com/nrohrbach/sharedmobility/blob/main/Sharedmobility.ch%20API.md#get-providers)
* [GET regions](https://github.com/nrohrbach/sharedmobility/blob/main/Sharedmobility.ch%20API.md#get-regions)

## GET attributes
Use the [attributes](https://api.sharedmobility.ch/documentation#/v1/getAttributes) endpoint to receive a list with available filters for [find](https://github.com/nrohrbach/sharedmobility/blob/main/Sharedmobility.ch%20API.md#get-find) and [identify](https://github.com/nrohrbach/sharedmobility/blob/main/Sharedmobility.ch%20API.md#get-identify) endpoints.

E.G: [Get all available attributes](https://api.sharedmobility.ch/v1/sharedmobility/attributes)
```
https://api.sharedmobility.ch/v1/sharedmobility/attributes
```
 
The following attributes are available:
| Attribute | Description |
| --------------- | --------- |
| ch.bfe.sharedmobility.provider.id | Provider Id according to [providers.json](https://sharedmobility.ch/providers.json) |
| ch.bfe.sharedmobility.pickup_type | System mode (free_floating or station_based) |
| ch.bfe.sharedmobility.vehicle_type | Vehicle type of a system |


Attributes to query station_based systems
| Attribute | Description |
| --------------- | --------- |
| ch.bfe.sharedmobility.available | Availability of a station |
| ch.bfe.sharedmobility.station.id | Id of a station |
| ch.bfe.sharedmobility.station.postcode | ZIP code of a station. Note that not all stations have postcode information |
| ch.bfe.sharedmobility.station.region.id | Id of a systems regions. Note that not all systems have region information |
| ch.bfe.sharedmobility.station.status.installed | If *true* a Station is installed on the street |
| ch.bfe.sharedmobility.station.status.renting | If *true* a Station is renting vehicles. Even if the station is empty |

Attributes to query free_floating systems
| Attribute | Description |
| --------------- | --------- |
| ch.bfe.sharedmobility.vehicle.status.disabled | If *true* a vehicle is currently disabled |
| ch.bfe.sharedmobility.vehicle.status.reserved | If *true* a vehicle is currently reserved |

## GET find
Use the [find](https://api.sharedmobility.ch/documentation#/v1/getFind) endpoint for a fulltext search in *station name* and *station address*.

E.G: [Get all stations with name "ETH Hönggerberg"](https://api.sharedmobility.ch/v1/sharedmobility/find?searchText=ETH%20H%C3%B6nggerberg&searchField=ch.bfe.sharedmobility.station.name&offset=0&geometryFormat=esrijson)
```
https://api.sharedmobility.ch/v1/sharedmobility/find?
searchText=ETH Hönggerberg
&searchField=ch.bfe.sharedmobility.station.name
&offset=0
&geometryFormat=esrijson
```

E.G: [Get all "Rent_a_bike" stations which contain "Bahnhof"](https://api.sharedmobility.ch/v1/sharedmobility/find?filters=ch.bfe.sharedmobility.provider.id%3Drent_a_bike&searchText=SBB&searchField=ch.bfe.sharedmobility.station.name&offset=0&geometryFormat=esrijson)
```
https://api.sharedmobility.ch/v1/sharedmobility/find?filters=ch.bfe.sharedmobility.provider.id=rent_a_bike
&searchText=SBB
&searchField=ch.bfe.sharedmobility.station.name
&offset=0
&geometryFormat=esrijson
```

E.G: [Get all E-Bikes from provider "publiebike" with station name "Mittelstrasse"](https://api.sharedmobility.ch/v1/sharedmobility/find?filters=ch.bfe.sharedmobility.vehicle_type%3DE-Bike&filters=ch.bfe.sharedmobility.provider.id%3Dpubliebike&searchText=Mittelstrasse&searchField=ch.bfe.sharedmobility.station.name&offset=0&geometryFormat=esrijson )
```
https://api.sharedmobility.ch/v1/sharedmobility/find?
filters=ch.bfe.sharedmobility.vehicle_type=E-Bike
&filters=ch.bfe.sharedmobility.provider.id=publiebike
&searchText=Mittelstrasse
&searchField=ch.bfe.sharedmobility.station.name
&offset=0
&geometryFormat=esrijson 
```
## GET identify

## GET providers

## GET regions


