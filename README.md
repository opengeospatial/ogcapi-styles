# OGC API - Styles

This GitHub repository contains [OGC](http://opengeospatial.org)'s proposed standard for accessing styles for rendering geospatial data (features or coverages) on the web, "OGC API - Styles". The editor's draft of the specification can be found at [docs.opengeospatial.org/DRAFTS/20-009.html](https://docs.ogc.org/DRAFTS/20-009.html).

[OGC API standards](https://ogcapi.ogc.org) define modular API building blocks to spatially enable Web APIs in a consistent way. [OpenAPI](http://openapis.org) is used to define the reusable API building blocks with responses in JSON and HTML.

The OGC API family of standards is organized by resource type. OGC API Styles specifies API building blocks for interacting with styles in multiple style encodings and with metadata for the styles.

The work on the API started in the Open Portrayal Framework thread of OGC Testbed-15 with the results documented in an [Engineering Report](http://docs.opengeospatial.org/per/19-010r2.html).

## Overview

OGC API Styles supports several types of consumers, mainly:

* Visual style editors that create, update and delete styles for datasets that are shared by other Web APIs implementing OGC API Features, OGC API Tiles, or OGC API Coverages;
* Web APIs implementing OGC API Maps fetch styles and render spatial data (features or coverages) on the server;
* Map clients that fetch styles and render spatial data on the client.

The API building blocks implement three main concepts:

* **Styles** are the main resources.
* Each style is available as one or more **stylesheets** - the representation of a style in an encoding like OGC SLD 1.0 or Mapbox Style. Clients will use the stylesheet of a style that fits best based on the capabilities of available tools and their preferences.
* For each style there is **style metadata** available, with general descriptive information about the style, structural information (e.g., layers and attributes), and so forth to allow users to discover and select existing styles for their data.

```
GET /styles
```

Lists the styles available on the server, and each describes basic information about the geospatial data collection, like its id, title and description, as well as the available stylesheets.

```
GET /styles/topographic/metadata
```

Requests the metadata for the style "topographic" so that a client has more information about a potential style of interest. The response format (typically HTML or JSON, but extensions can easily supply others) is determined using [HTTP content negotiation](https://restfulapi.net/content-negotiation/).

```
GET /styles/topographic
```

Returns a stylesheet. Again, if multiple encodings are available, the style encoding is determined using [HTTP content negotiation](https://restfulapi.net/content-negotiation/).

In order to support styles, clients of data APIs (for example, supporting OGC API Features and/or OGC API Tiles) benefit from additional capabilities in these APIs, too. These are:

* List and manage the applicable styles per collection (path `/collections/{collectionId}`).
* Fetch the queryables of a collection (path `/collections/{collectionId}/queryables`) to support clients such as visual style editors to construct expressions for selection criteria in queries on features in the collection. "Queryable" means that the property may be used in styling rules or other filter expressions.

To support styling of coverage data, additional capabilities in the data API may be required, but have not been investigated yet.

## Using the specification

The editor's draft is on the OGC website:

* [Editor's Draft of OGC API - Styles](http://docs.opengeospatial.org/DRAFTS/20-009.html)

A [PDF version](http://docs.opengeospatial.org/DRAFTS/20-009.pdf) is available, too.

If you prefer to view sample API definitions to get an idea, have a look at the following OpenAPI definitions on SwaggerHub (from Testbed-15):

* [Styles API](https://app.swaggerhub.com/apis/cportele/opf-style-api/1.0.0)
* [Features API with style extensions](https://app.swaggerhub.com/apis/cportele/opf-features-api/1.0.0)

Several implementations of the draft standard exist:

* [Implementations of the draft specification / demo services](implementations.md)

## Communication

Most of the work on the specification takes place in [GitHub issues](https://github.com/opengeospatial/ogcapi-styles/issues),
so browse there to get a good idea of what is happening, as well as past decisions.

## Additional information

The design principles of the specification is inspired by the work on [OGC API - Features](https://github.com/opengeospatial/ogcapi-features). For more information on the OGC API family of standards, see [ogcapi.org](http://ogcapi.org/).

More background information about OGC API Styles can be found in reports from OGC Testbed-15:
* [OGC Testbed-15: Open Portrayal Framework Engineering Report](http://docs.opengeospatial.org/per/19-018.html)
* [OGC Testbed-15: Encoding and Metadata Conceptual Model for Styles Engineering Report](http://docs.opengeospatial.org/per/19-023r1.html)
* [OGC Testbed-15: Styles API Engineering Report](http://docs.opengeospatial.org/per/19-010r2.html)

## Building

The latest drafts of each standard in this repository are build daily (based on the configuration contained in the [asciidoctor.json](https://github.com/opengeospatial/ogcapi-features/blob/master/asciidoctor.json) file):

* [OGC API - Styles](http://docs.opengeospatial.org/DRAFTS/20-009.html)

To generate the HTML versions of the standards from this repository yourself, ensure that you have [Ruby](https://www.ruby-lang.org/en/) and
[Asciidoctor](https://asciidoctor.org/) set up and [installed](https://asciidoctor.org/docs/#get-started-with-asciidoctor).
Then run:

```
asciidoctor standard/20-009.adoc
```

The resulting HTML files will be built in the same directory as the AsciiDoc file, e.g. as `standard/20-009.html`.

## Contributing

The contributor understands that any contributions, if accepted by the OGC Membership, shall be incorporated into OGC standards documents and that all copyright and intellectual property shall be vested to the OGC.

The OGC API Styles Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is working to do as much work in public as possible.

* [Open issues](https://github.com/opengeospatial/ogcapi-styles/issues)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/ogcapi-styles/master/LICENSE)

For more information, see [CONTRIBUTING.md](CONTRIBUTING.md).

Pull Requests from contributors are welcomed. However, please note that by sending a Pull Request or Commit to this GitHub repository, you are agreeing to the terms in the Observer Agreement https://portal.ogc.org/files/?artifact_id=92169
