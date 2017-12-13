# Point of interest (Malatya use case of SMART-FI Project)

## Description

This entity contains a harmonised geographic description of a Point of Interest for Malatya use case of SMART-FI Project. This data model has been created in cooperation with the GSMA and the members of the [IoT Big Data Project](http://www.gsma.com/iot/iot-big-data/). 

## Data Model

A JSON Schema corresponding to this data model can be found [here](http://fiware.github.io/dataModels/PointOfInterest/PointOfInterest/MalatyaPointOfInterestModel/schema.json)

+ `id` : Unique identifier. 

+ `type` : Entity type. It must be equal to `PointOfInterest`.

+ `dateModified` : Last update timestamp of this entity.
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional

+ `dateCreated` : Entity's creation timestamp.
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional
    
+ `source` : A sequence of characters giving the source of the entity data.
    + Attribute type: [Text](https://schema.org/Text) or [URL](https://schema.org/URL)
    + Optional    
    
+ `name` : Name of this point of interest.
    + Normative References: [https://schema.org/name](https://schema.org/name)
    + Mandatory
    
+ `alternateName` : Alternative name for this point of interest.
    + Normative References: [https://schema.org/alternateName](https://schema.org/alternateName)
    + Optional

+ `description` : Description of this point of interest.
    + Normative References: [https://schema.org/description](https://schema.org/description]
    + Optional

+ `location` : Location of the point of interest represented by a GeoJSON geometry, usually a `Point`. 
    + Attribute type: `geo:json`.
    + Normative References: [https://tools.ietf.org/html/rfc7946](https://tools.ietf.org/html/rfc7946)
    + Mandatory if `address` is not defined. 
    
+ `address` : Civic address of this point of interest.
    + Normative References: [https://schema.org/address](https://schema.org/address)
    + Mandatory if `location` is not present.
    
+ `category` : Category of this point of interest. 
    + Attribute type: List of text [Text](https://schema.org/Text)
    + Allowed values: Those defined by the [Factual taxonomy](https://github.com/Factual/places/blob/master/categories/factual_taxonomy.json).
    For instance the value `113` corresponds to beaches, and the value `311` corresponds to museums. 
    + Mandatory
    
+ `refSeeAlso` : Reference to one or more related entities that may provide extra,
specific information about this point of interest.
    + Attribute type: List of References
    + Optional
    
## Examples of use

    {
        "id": "PointOfInterest-64933",
        "type": "PointOfInterest",
        "name": "ÇİÇEK TİCARET",
        "description": "Birbirinden farklı ve çeşit dolu bakır süs ve mutfak eşyalarının bulundu",
        "address": {
          "addressCountry": "TR",
          "addressLocality": "Dabakhane Mahallesi, Yeni Boztepe  7 A, Malatya Merkez/Malatya"
        },
        "category": ["178"],
        "location": {
          "type": "Point",
          "coordinates": [
            38.3506807929027,
            38.3166412407296
          ]
        },
        "source": "Malatya Metropolitan Municipality",
        "refSeeAlso": [""]
    }

    
