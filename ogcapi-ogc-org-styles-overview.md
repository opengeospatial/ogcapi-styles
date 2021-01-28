# OGC API - Styles

[OGC API standards](https://ogcapi.ogc.org/) define modular API building blocks to spatially enable Web APIs
in a consistent way. [OpenAPI](http://openapis.org) is used to define the reusable
API building blocks with responses in JSON and HTML.

The OGC API family of standards is organized by resource type. OGC API - Styles specifies building blocks for Web APIs that enable map servers and clients as well as visual style editors to manage and fetch styles.

## Overview of OGC API - Styles - Part 1: Core

```
GET /
```

Retrieves the landing page. The purpose of the landing page is to provide clients with a starting point for using the API. Any resource exposed through an API can be accessed by following paths or links starting from the landing page.


```
GET {root}/conformance
```

Provides a list declaring the modules that are implemented by the API. These modules are referred to as Conformance Classes. The list of Conformance Classes is key to understanding and using an OGC Web API.

```
GET /styles
```

Fetch styles.

```
POST /styles
```

Can be used to create or validate styles.


```
GET /styles/{styleId}
```

Fetch a style.


```
PUT /styles/{styleId}
```

Can be used to update, create or validate a style.

```
DELETE /styles/{styleId}
```

Delete a style.

```
GET /styles/{styleId}/metadata
```

Fetch style metadata.

```
PUT /styles/{styleId}
```

Replace the metadata of a style.

```
PATCH /styles/{styleId}
```

Update parts of the metadata of a style.


```
GET /resources
```

Fetch resources.

```
GET /resources/{resourceId}
```

Fetch a resource.

```
PUT /resources/{resourceId}
```

Create or replace a resource

```
DELETE /resources/{resourceId}
```

Delete a resource.
