
# End User IDs Schema

```
https://ns.adobe.com/xdm/context/enduserids
```

The End User IDs schema is used to represent a federated identity of a visitor or known profile across a number of data sources.

It is an `object` that is using the `@id` of an XDM data source as keys. 
Each value consists of the (required) ID that is native to the data source, and (optional) metadata about the data source as well as (optional) confidence in the stitching.

Additionally, this schema can include a property that describes the data source that is responsible for identity stitching.


| Abstract | Extensible | Custom Properties | Additional Properties | Defined In |
|----------|------------|-------------------|-----------------------|------------|
| Can be instantiated | Yes | Forbidden | Permitted | [context/enduserids.schema.json](context/enduserids.schema.json) |

## Schema Hierarchy

* End User IDs `https://ns.adobe.com/xdm/context/enduserids`
  * [Data Source](../data/datasource.schema.md) `https://ns.adobe.com/xdm/data/datasource`

## End User IDs Example
```json
{
  "xdm:realm": {
    "@id": "https://data.adobe.io/experiencecloud/audiencemanager",
    "xdm:name": "Adobe Audience Manager"
  },
  "https://ns.adobe.com/experiencecloud/mcid": {
    "xdm:datasource": {
      "@id": "https://data.adobe.io/experiencecloud/mcid",
      "xdm:name": "Adobe Marketing Cloud Identity Core Service"
    },
    "xdm:id": "mcid-sample111",
    "xdm:confidence": 1
  },
  "https://ns.adobe.com/experiencecloud/analytics": {
    "xdm:id": "mcid-sample111",
    "xdm:confidence": 0.99
  }
}
```

# End User IDs Properties

| Property | Type | Required | Defined by |
|----------|------|----------|------------|
| [xdm:realm](#xdmrealm) | Data Source | Optional | End User IDs (this schema) |
| `.+://.+` | `object` | Pattern | End User IDs (this schema) |
| `*` | any | Additional | this schema *allows* additional properties |

## xdm:realm
### Realm

The optional realm associated with the identity stitching strategy.

`xdm:realm`
* is optional
* type: Data Source
* defined in this schema

### xdm:realm Type


* [Data Source](../data/datasource.schema.md) – `https://ns.adobe.com/xdm/data/datasource`





## Pattern: `.+://.+`
Applies to all properties that match the regular expression `.+://.+`


The identifier, including data source (`@id` must be identical to the property value), foreign ID, and confidence.

`.+://.+`
* is a property pattern
* type: `object`
* defined in this schema

### Pattern .+://.+ Type

Unknown type `object`.

```json
{
  "meta:enum": {
    "https://ns.adobe.com/experiencecloud/target": "Adobe Target",
    "https://ns.adobe.com/experiencecloud/campaign": "Adobe Campaign",
    "https://ns.adobe.com/experiencecloud/analytics": "Adobe Analytics",
    "https://ns.adobe.com/experiencecloud/mcid": "Marketing Cloud Identity Core Service"
  },
  "description": "The identifier, including data source (`@id` must be identical to the property value), foreign ID, and confidence.",
  "type": "object",
  "properties": {
    "xdm:datasource": {
      "$ref": "https://ns.adobe.com/xdm/data/datasource"
    },
    "xdm:id": {
      "type": "string",
      "description": "The ID that is being used by the service specified by the outer property name or `xdm:datasource`\n\n. **Note:** opposed to most other IDs in XDM, this is not a URI, as it cannot be guaranteed that all identity services are using URIs as IDs."
    },
    "xdm:confidence": {
      "type": "number",
      "minimum": 0,
      "maximum": 1
    }
  },
  "required": [
    "xdm:id"
  ],
  "simpletype": "`object`"
}
```


### Pattern .+://.+ Known Values
| Value | Description |
|-------|-------------|
| `https://ns.adobe.com/experiencecloud/target` | Adobe Target |
| `https://ns.adobe.com/experiencecloud/campaign` | Adobe Campaign |
| `https://ns.adobe.com/experiencecloud/analytics` | Adobe Analytics |
| `https://ns.adobe.com/experiencecloud/mcid` | Marketing Cloud Identity Core Service |




# End User IDs Definitions

| Property | Type | Group |
|----------|------|-------|
| [xdm:analytics](#xdm:analytics) | reference | `https://ns.adobe.com/xdm/context/enduserids#/definitions/enduserids` |
| [xdm:campaign](#xdm:campaign) | reference | `https://ns.adobe.com/xdm/context/enduserids#/definitions/enduserids` |
| [xdm:mcId](#xdm:mcId) | reference | `https://ns.adobe.com/xdm/context/enduserids#/definitions/enduserids` |
| [xdm:realmId](#xdm:realmId) | complex | `https://ns.adobe.com/xdm/context/enduserids#/definitions/enduserids` |
| [xdm:target](#xdm:target) | reference | `https://ns.adobe.com/xdm/context/enduserids#/definitions/enduserids` |

## xdm:analytics
### Analytics

Adobe Analytics end user identifier.

`xdm:analytics`
* is optional
* type: reference
* defined in this schema

### xdm:analytics Type


* []() – `https://ns.adobe.com/xdm/context/identity`





## xdm:campaign
### Campaign

Adobe Campaign profile identifier.

`xdm:campaign`
* is optional
* type: reference
* defined in this schema

### xdm:campaign Type


* []() – `https://ns.adobe.com/xdm/context/identity`





## xdm:mcId
### Marketing Cloud identifier

A unique identifier from Adobe Marketing Cloud.

`xdm:mcId`
* is optional
* type: reference
* defined in this schema

### xdm:mcId Type


* []() – `https://ns.adobe.com/xdm/context/identity`





## xdm:realmId


`xdm:realmId`
* is optional
* type: complex
* defined in this schema

### xdm:realmId Type

Unknown type ``.

```json
{
  "definitiongroup": "enduserids",
  "simpletype": "complex"
}
```





## xdm:target
### Target

Adobe Target end user identifier.

`xdm:target`
* is optional
* type: reference
* defined in this schema

### xdm:target Type


* []() – `https://ns.adobe.com/xdm/context/identity`




