# yammdb
just another .mmdb

This is another .mmdb which initially is build to verify existing geo data with real measurements.<br>
However it works like any other .mmdb you can find on the Internet.<br>

The goal is to update this .mmdb weekly.<br>
You can get the .mmdb here: https://yammdb.b-cdn.net/geo.mmdb<br>

**Limitations**<br>
- This is not convering the entire IPv4 space, roughtly from 800k routed subnets, we have data on about 600k.
- 1.1.1.1 like any other anycast IP will return incorrect data, the IP has to be unicast

**Locations**<br>
Currently we have Servers in the following locations, we use to take measurements.<br>
| Country          | City          | Info   |
| ------------- | ------------- | ------------- |
|NL             | Amsterdam     |               |
|AT             | Vienna        |               |
|SE             | Stockholm     |               |
|US             | New York      |               |
|US             | Seattle       |               |
|US             | Miami         |               |
|SG             | Singapore     |               |
|JP             | Tokyo         |               |
|CN             | Hong Kong     | CN2           |

This list will likely be expanded, if you want to sponsor us a virtual server for this, you can hit me up.<br>

**Structure**<br>
The Datastructure is the following.<br>
| Name          | Type          | Description   |
| ------------- | ------------- | ------------- |
| country       | string        | ISO 3166-1, Alpha2 |
| location(latitude,longitude) | double   | WGS |  

**Example**<br>
Reading the data is as easy as:
```
import geoip2.database
reader = geoip2.database.Reader("geo.mmdb")

response = reader.city("1.1.1.1")
print(response.country,response.location.latitude,response.location.longitude)
```