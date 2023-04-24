# yammdb
just another .mmdb

This is another .mmdb which initially is build to verify existing geo data with real measurements.<br>
However it works like any other .mmdb you can find on the Internet.<br>

The goal is to update this .mmdb weekly.<br>

Currently we have a Server in the following locations we use to take measurements.<br>
- NL, Amsterdam
- AT, Vienna
- SE, Stockholm
- US, New York
- US, Seattle
- US, Miami
- SG, Singapore
- JP, Tokyo
- CN, Hong Kong (CN2)

This list will likely be expanded, if you want to sponsor us a virtual server for this, you can hit me up.<br>

The Datastructure is the following.<br>
| Name          | Type          | Description   |
| ------------- | ------------- | ------------- |
| country       | string        | ISO 3166-1, Alpha2 |
| location(latitude,longitude) | double   | WGS |  
