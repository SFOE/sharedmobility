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
 
