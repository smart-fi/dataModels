# Commuter

## Description

A citizen travelling between different points in the city.

## Data Model

+ `id` : Entity's unique identifier. 

+ `type` : Entity type. It must be equal to `Commuter`.

+ `username` : User name for this commuter. 
    + Normative References: [https://schema.org/name](https://schema.org/name)
    ## consider https://schema.org/text instead of https://schema.org/name
    + Optional

+ `location` : Commuter's last known location represented by a GeoJSON Point. 
    + Attribute type: `geo:json`.
    + Normative References: [https://tools.ietf.org/html/rfc7946](https://tools.ietf.org/html/rfc7946)
    + Attribute metadata:
        + `timestamp`: Timestamp which captures when the commuter was at that location.
        This value can also appear as a FIWARE [TimeInstant](https://github.com/telefonicaid/iotagent-node-lib/blob/develop/README.md#TimeInstant)
            + Type: [DateTime](http://schema.org/DateTime) or `ISO8601` (legacy).
            + Mandatory
    + Mandatory

+ `route` : Structured attribute that includes all the attributes for the suggested route.
    + Attribute type: `structured`.
    + Optional

+ `start` : Starting point of the suggested route, represented by a GeoJSON Point. 
    + Attribute type: `geo:json`.
    + Normative References: [https://tools.ietf.org/html/rfc7946](https://tools.ietf.org/html/rfc7946)
    + Mandatory if route is included

+ `end` : End point of the suggested route, represented by a GeoJSON Point. 
    + Attribute type: `geo:json`.
    + Normative References: [https://tools.ietf.org/html/rfc7946](https://tools.ietf.org/html/rfc7946)
    + Mandatory if route is included
    
+ `transportation` : Structured attribute that includes all the attributes for the suggested route.
    + Attribute type: `structured`.
    + Mandatory if route is included    
    
+ `estimatedDistance` : Denotes the estimated distance for the suggested route and is specified in Kilometers.
If provided, the value of the distance attribute must be a non-negative real number. `null` *MAY* be used if `distance` is transiently unknown for some reason.    
    + Attribute type: [Number](https:/schema.org/Number)
    + Default unit: Kilometers
    + Optional
    
+ `estimatedTime` : Denotes the estimated duration for the suggested route and is specified in minutes.
If provided, the value of the timeestimated attribute must be a non-negative real number. `null` *MAY* be used if `timestimated` is transiently unknown for some reason.    
    + Attribute type: [Number](https:/schema.org/Number)
    + Default unit: Minutes
    + Optional
    
+ `confirmed` : Denotes whether the commuter has confirmed in their mobile app that they have taken the suggested route and is specified as strings Yes or No.
If provided, the value of the confirmed  attribute must be the strings Yes or No. 
    + Attribute type: [Number](https:/schema.org/Text)
    + Optional    
    
+ `dateModified` : Last update timestamp of this entity.
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional

+ `dateCreated` : Creation timestamp of this entity.
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional
    
## Example

    {
      "id": "commuter:johnb:25",
      "type": "Commuter",
      "username": "johnb",
      "location": {
         "type": "Point",
         "coordinates": [ -3.164485591715449, 40.62785133667262 ]
      },
      "route": {
        "start": {
            "type": "Point",
             "coordinates": [ -3.164485591715449, 40.62785133667262 ]
        },
        "end": {
            "type": "Point",
             "coordinates": [ -3.164485591715449, 40.62785133667262 ]
        },
        "transportation": {
            "transportationType": "Bus",
            "busRouteNumbers": [21A, 32T, 40B],
        },
        "estimatedDistance": 17,
        "estimatedTime": 25,
        "confirmed": yes
      },
      "dateModified" : 2016-10-25T16:52:32,
      "dateCreated" : 2016-10-25T16:22:25
    }
    
## Test it with a real service

T.B.D.

## Issues

* Not sure how to represent structured values such as route and transportation in the data model description. 
The other FIWARE data models at https://github.com/Fiware/dataModels do not seem to have examples for nested attributes (excpet for the structured values that are already defined in schema.org, ietf, etc.)

* Not sure if the date/time example I added is correct based on https://schema.org/DateTime
 