# Access sharedmobility.ch data using the REST API
The data of the [GBFS-endpoint](https://sharedmobility.ch/gbfs.json) of [sharedmobility.ch](https://www.sharedmobility.ch/) can be accessed with a RESTful API. 
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
 
**Available attributes:** 
| Attribute | Description |
| --------------- | --------- |
| ch.bfe.sharedmobility.provider.id | Provider Id according to [providers.csv](https://github.com/nrohrbach/sharedmobility/blob/main/providers.csv) |
| ch.bfe.sharedmobility.pickup_type | System mode (*free_floating* or *station_based*) |
| ch.bfe.sharedmobility.vehicle_type | Vehicle type of a system |


**Attributes to query station_based systems:**
| Attribute | Description |
| --------------- | --------- |
| ch.bfe.sharedmobility.available | Availability of a station |
| ch.bfe.sharedmobility.station.id | Id of a station |
| ch.bfe.sharedmobility.station.postcode | ZIP code of a station. Note that not all stations have postcode information |
| ch.bfe.sharedmobility.station.region.id | Id of a systems regions. Note that not all systems have region information |
| ch.bfe.sharedmobility.station.status.installed | If *true* a station is installed on the street |
| ch.bfe.sharedmobility.station.status.renting | If *true* a station is renting vehicles. Even if the station is empty |

**Attributes to query free_floating systems:**
| Attribute | Description |
| --------------- | --------- |
| ch.bfe.sharedmobility.vehicle.status.disabled | If *true* a vehicle is currently disabled |
| ch.bfe.sharedmobility.vehicle.status.reserved | If *true* a vehicle is currently reserved |

## GET find
Use the [find](https://api.sharedmobility.ch/documentation#/v1/getFind) endpoint for a fulltext search in *station name* and *station address*.

E.G: [Get all stations with station name "ETH Hönggerberg"](https://api.sharedmobility.ch/v1/sharedmobility/find?searchText=ETH%20H%C3%B6nggerberg&searchField=ch.bfe.sharedmobility.station.name&offset=0&geometryFormat=esrijson)
```
https://api.sharedmobility.ch/v1/sharedmobility/find?
searchText=ETH Hönggerberg
&searchField=ch.bfe.sharedmobility.station.name
&offset=0
&geometryFormat=esrijson
```

E.G: [Get all stations from provider "Rent_a_bike" with station name "Bahnhof"](https://api.sharedmobility.ch/v1/sharedmobility/find?filters=ch.bfe.sharedmobility.provider.id%3Drent_a_bike&searchText=Bahnhof&searchField=ch.bfe.sharedmobility.station.name&offset=0&geometryFormat=esrijson)
```
https://api.sharedmobility.ch/v1/sharedmobility/find?
filters=ch.bfe.sharedmobility.provider.id=rent_a_bike
&searchText=Bahnhof
&searchField=ch.bfe.sharedmobility.station.name
&offset=0
&geometryFormat=esrijson
```

E.G: [Get all stations with E-Bikes from provider "publiebike" with station name "Mittelstrasse"](https://api.sharedmobility.ch/v1/sharedmobility/find?filters=ch.bfe.sharedmobility.vehicle_type%3DE-Bike&filters=ch.bfe.sharedmobility.provider.id%3Dpubliebike&searchText=Mittelstrasse&searchField=ch.bfe.sharedmobility.station.name&offset=0&geometryFormat=esrijson )
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
Use the [identify](https://api.sharedmobility.ch/documentation#/v1/getIdentify) endpoint for spatial queries.

E.G: [Get all available vehicles which are within 200m around point 8.72334 47.50024](https://api.sharedmobility.ch/v1/sharedmobility/identify?Geometry=8.72334%2C47.50024&Tolerance=200&offset=0&geometryFormat=esrijson)
```
https://api.sharedmobility.ch/v1/sharedmobility/identify?
Geometry=8.72334,47.50024
&Tolerance=200
&offset=0
&geometryFormat=esrijson
```

E.G: [Get all available E-Scooter which are within 500m around point 8.72334 47.50024](https://api.sharedmobility.ch/v1/sharedmobility/identify?filters=ch.bfe.sharedmobility.vehicle_type%3DE-Scooter&Geometry=8.72334%2C47.50024&Tolerance=500&offset=0&geometryFormat=esrijson)
```
https://api.sharedmobility.ch/v1/sharedmobility/identify?
filters=ch.bfe.sharedmobility.vehicle_type=E-Scooter
&Geometry=8.72334,47.50024
&Tolerance=500
&offset=0
&geometryFormat=esrijson
```


E.G: [Get all available station-based E-Bikes which are within 5000m around 7.57699,47.55352](https://api.sharedmobility.ch/v1/sharedmobility/identify?filters=ch.bfe.sharedmobility.vehicle_type%3DE-Bike&filters=ch.bfe.sharedmobility.pickup_type%3Dstation_based&Geometry=7.57699%2C47.55352&Tolerance=5000&offset=0&geometryFormat=esrijson)
```
https://api.sharedmobility.ch/v1/sharedmobility/identify?
filters=ch.bfe.sharedmobility.vehicle_type=E-Bike
&filters=ch.bfe.sharedmobility.pickup_type=station_based
&Geometry=7.57699,47.55352
&Tolerance=5000
&offset=0
&geometryFormat=esrijson
```

Note: You can use the [SearchServer](https://api3.geo.admin.ch/services/sdiservices.html#search) of the [GeoAdmin API](https://www.bfe.admin.ch/bfe/en/home/supply/statistics-and-geodata/geoinformation/programming-interfaces/geoadmin-api.html) to get the coordinates of an address (see [step 1 of GeoAdmin documentation](https://github.com/SFOE/geo-api-documentation#1-get-the-coordinates-of-an-address)).

## GET providers
Use the [providers](https://api.sharedmobility.ch/documentation#/v1/getProviders) endpoint to get details about shared mobility providers.

E.G: [Get a list of all providers](https://api.sharedmobility.ch/v1/sharedmobility/providers)
```
https://api.sharedmobility.ch/v1/sharedmobility/providers
```

E.G: [Get details of provider *donkey_thun*](https://api.sharedmobility.ch/v1/sharedmobility/providers)
```
https://api.sharedmobility.ch/v1/sharedmobility/providers/donkey_thun
```
Note: Provider_id is according to [providers.csv](https://github.com/nrohrbach/sharedmobility/blob/main/providers.csv)

## GET regions
Use the [regions](https://api.sharedmobility.ch/documentation#/v1/getRegions) endpoint to get details about shared mobility regions.

E.G: [Get a list of all regions](https://api.sharedmobility.ch/v1/sharedmobility/regions)
```
https://api.sharedmobility.ch/v1/sharedmobility/regions
```

E.G: [Get details of region *emobility:968*](https://api.sharedmobility.ch/v1/sharedmobility/regions/emobility%3A968)
```
https://api.sharedmobility.ch/v1/sharedmobility/regions/emobility:968
```

Note that not all systems have region information
