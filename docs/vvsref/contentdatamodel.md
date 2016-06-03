# The Content Data Model

The Content Data Model is for `contentResources`.  It is described below.  The optional `sources` property of the Content Data model is an array.  It is described further below.

## The Model

The Content Data Model is described in the table below:  

| property | default | type | description | example |
|----------|---------|------|-------------|---------|
| id | `null` | String | Identifier for the content. | `'12345'` |
| sources (optional) | `null` | [Source](#source) []| Array that contains information about all possible sources, where each source consists of a `mimetype` and a `url`. Other optional parameters are: `protocol`, `cdn` or `bitrate`. Player will then select the most appropriate source for displaying. Each parameter is described in more detail in the table below. | `[{ url: '.',`<br>`mimetype:`<br>`'.'`<br>`}]` |
| duration | `null` | Float | Duration of the video | `120` |
| title | `null` | String | Title of the content | `'My video`<br>`title'` |


## The Sources Attribute
The sources property in the table above can have the following valid values:

| property | default | type | description | example | possible values |
|----------|---------|------|-------------|---------|-----------------|
| url | `null` | String | URL of the source. | `'http://foo.mp4'` ||
| mimetype | `null` | String | Mimetype of the source. | `'video/mp4'` ||
| protocol (optional) | `null` | String | Protocol of the source. | `'http'` | `'http'` or `'rtmp'` |
| cdn (optional) | `null` | String | Control Delivery Network (CDN) from which the source originates. | `'level3'` ||
| bitrate (optional) | `null` | uint | Bitrate of the source. | `1200000` ||