# Additions to GBFS

Sharedmobility.ch is based on the [General Bikeshare Feed Specification (GBFS)](https://github.com/SFOE/sharedmobility/blob/main/Access%20the%20data.md) an open specification, developed and maintained by the community of produders and consumers of GBFS data.
GBFS is optimized to represent one system. In order to represent multiple systems in one feed, the following additions to GBFS V2.0 were made:

## Add providers.json



## Differences
* According to GBFS V2 the field bike_id in free_bike_status.json has to be rotated to a random string, at a minimum, after each trip to protect privacy. This is not fully supported by all providers.
