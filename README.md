# yammdb
just another .mmdb

This is another .mmdb which initially is build to verify existing geo data with real measurements.<br>
However it works like any other .mmdb you can find on the Internet.<br>

The goal is to update this .mmdb weekly.<br>
You can get the .mmdb here: https://yammdb.serv.app/geo.mmdb<br>

**Limitations**<br>
- This is not convering the entire IPv4 space, roughtly from 975k routed subnets, we have data on about 717k.
- 1.1.1.1 like any other anycast IP will return incorrect data, the IP has to be unicast

**Locations**<br>
Currently we have Servers in the following locations, we use to take measurements.<br>
| Country          | City          | Info   |
| ------------- | ------------- | ------------- |
|NL             | Amsterdam     |               |
|DE             | Frankfurt     |               |
|CZ             | Prague        | [Thanks to Skylonhost](https://skylonhost.com) |
|PL             | Warsaw        | [Thanks to Webhorizon](https://webhorizon.net) |
|AT             | Vienna        |               |
|ES             | Madrid        | [Thanks to Ginernet](https://ginernet.com) |
|SE             | Stockholm     |               |
|RU             | Moscow        |               |
|RU             | Novosibirsk   |               |
|US             | New York      |               |
|US             | Seattle       |               |
|US             | Miami         |               |
|US             | Dallas        |               |
|BR             | Sao Paulo     | [Thanks to Misaka](https://www.misaka.io) |
|PK             | Pakistan      | [Thanks to Virtury](https://virtury.com) |
|SG             | Singapore     |               |
|JP             | Tokyo         |               |
|CN             | Hong Kong     | CN2           |
|NG             | Lagos         | [Thanks to Misaka](https://www.misaka.io) |

This list will likely be expanded, if you want to sponsor us a virtual server for this, you can hit me up.<br>

**Structure**<br>
The Datastructure is the following.<br>
| Name                         | Type          | Description        |
| -------------                | ------------- | -------------      |
| iso_code                     | string        | ISO 3166-1, Alpha2 |
| continent_code               | string        | NA, EU, AS         |
| location(latitude,longitude) | double        | WGS                |
| accuracy_radius              | double        | latency (ms)       |    

**Example**<br>
Reading the data is as easy as:
```
import geoip2.database

reader = geoip2.database.Reader("geo.mmdb")
response = reader.city("1.1.1.1")
print("Continent",response.continent.code)
print("Country",response.country.iso_code)
print("Latitude",response.location.latitude,"Longitude",response.location.longitude)
print(f"Latency {response.location.accuracy_radius}ms")
```
Currently accuracy_radius is used for the latency measured, since custom fields are not possible in the default reader.