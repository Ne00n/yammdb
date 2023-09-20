# yammdb
just another .mmdb

This is another .mmdb which initially is build to verify existing geo data with real measurements.<br>
However it works like any other .mmdb you can find on the Internet.<br>

The goal is to update this .mmdb weekly.<br>
You can get the .mmdb here: https://yammdb.serv.app/geo.mmdb<br>
Raw data can be found here: https://raw.serv.app/<br>

**Limitations**<br>
- This is not convering the entire IPv4 space, roughtly from 975k routed subnets, we have data on about 717k.
- 1.1.1.1 like any other anycast IP will return incorrect data, the IP has to be unicast

**Locations**<br>
Currently we have Servers in the following locations, we use to take measurements.<br>

| Continent     | Country       | City          | Info          |
| ------------- | ------------- | ------------- | ------------- |
|EU             |NL             | Amsterdam     |               |
|EU             |DE             | Frankfurt     |               |
|EU             |FR             | Paris         | [Thanks to Bunny](https://bunny.net) |
|EU             |CZ             | Prague        | [Thanks to Skylonhost](https://skylonhost.com) |
|EU             |PL             | Warsaw        | [Thanks to Webhorizon](https://webhorizon.net) |
|EU             |AT             | Vienna        |               |
|EU             |CH             | Zurich        |               |
|EU             |ES             | Madrid        | [Thanks to Ginernet](https://ginernet.com) |
|EU             |RU             | Moscow        |               |
|EU             |TR             | Istanbul      | [Thanks to Rabisu](https://rabisu.com) |
|NA             |US             | New York      |               |
|NA             |US             | Seattle       |               |
|NA             |US             | Miami         |               |
|NA             |US             | Dallas        |               |
|SA             |BR             | Sao Paulo     | [Thanks to Misaka](https://misaka.io) |
|AF             |NG             | Lagos         | [Thanks to Misaka](https://misaka.io) |
|AS             |RU             | Novosibirsk   |               |
|AS             |JP             | Tokyo         | CN2           |
|AS             |CN             | Hong Kong     | CN2           |
|AS             |SG             | Singapore     |               |
|OC             |AU             | Sydney        | [Thanks to Advinservers](https://advinservers.com) |
|AS             |PK             | Pakistan      | [Thanks to Virtury](https://virtury.com) |

This list will likely be expanded, if you want to sponsor us a virtual server for this, you can hit me up.<br>

**Structure**<br>
The Datastructure is the following.<br>
| Name                         | Type          | Description            |
| -------------                | ------------- | -------------          |
| iso_code                     | string        | ISO 3166-1, Alpha2     |
| continent_code               | string        | NA, SA, AF, EU, AS, OC |
| location(latitude,longitude) | double        | WGS                    |
| accuracy_radius              | double        | latency (ms)           |    

**Install dependencies for python example**<br>
```
pip3 install geoip2
```

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