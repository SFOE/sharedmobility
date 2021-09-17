# Access sharedmobility.ch data using the REST API
The data of the GBFS-endpoint of sharedmobility.ch can be accessed with a RESTful API. Here we show you some examples how to query the API.

## General information
* Swagger documentation: [api.sharedmobility.ch](https://api.sharedmobility.ch)

## Available endpoints
* GET attributes
* GET find
* GET identify
* GET providers
* GET regions

## GET attributes
Use the attributes endpint to receiv a list with available filters for find and identify endpoints.

E.G: [Get all available attributes](https://api.sharedmobility.ch/v1/sharedmobility/attributes)
```
https://api.sharedmobility.ch/v1/sharedmobility/attributes
```
 
The following attributes are available:
| Attribute | Description |
| --------------- | --------- |
| ch.bfe.sharedmobility.provider.id | Provider Id according to providers.json |
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


