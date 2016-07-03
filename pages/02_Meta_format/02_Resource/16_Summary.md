## Properties summary

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| @doctype | String | Yes | No | Document type |
| label | String | Yes | Yes | Label of resource |
| alises | Array of String | No | Yes | Alternative resource labels, eg. different forms of words - helpful for voice control |
| icon | String / URI | No | No | URI to resource icon, all image formats are supported but SVG is recommended |
| schema | String | No | No | MetaWEB schema identifier from [Schema vocabulary](../schema-vocabulary/) |
| readonly | Boolean / Model prop. as String | No | No | If resource is read-only and thus all controls must be disabled. |
| parent | String / URI | No | Yes | URI to parent resource |
| previous | String / URI | No | Yes | URI to previous resource on same navigation level |
| next | String / URI | No | Yes | URI to next resource on same navigation level |
| sitemap | String / URI | No | Yes | URI to MetaWEB sitemap file |
| manifest | String / URI | No | Yes | URI to MetaWEB application manifest file |
| properties | Array of Object | Yes | No | Properties definition |
| actions | Array of Object | No | No | Actions definition |
| template | String / URI | No | No | Template URI |
| $* | Object | No | No | Model property |