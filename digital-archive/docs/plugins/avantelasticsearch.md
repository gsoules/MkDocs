# AvantElasticsearch

Provides support for [Elasticsearch](https://aws.amazon.com/elasticsearch-service/)  hosted on Amazon AWS.

---

## Configuration options

AvantElasticsearch has these configuration options:

Contributor Id
:   Identification for this organization (3 to 6 lower case letters a-z)

Contributor
:   Organization name as it should be shown for the contributor of its data

Host
:   Example: search-something-xxxxxxxxxxxx.us-east-2.es.amazonaws.com

Region
:   AWS server region

Key
:   AWS Access Key Id

Secret
:   AWS Secret Access Key

Local Index
:   Enable local index

Shared Index
:   Enable shared index

See also the documentation for [installing AvantElasticsearch](../../../developer/install-digital-archive/#avantelasticsearch).

---

## Dependencies
The AvantElasticsearch plugin requires that the [AvantCommon] plugin be installed and activated.

This plugin was developed specifically for [Digital Archive](http://thedigitalarchive.net/) installations. It has special
knowledge of the following Omeka elements and how they are used in these installations.

-   **_Type_**
-   **_Subject_**
-   **_Place_**
-   **_Address_**
-   **_Date_**

This AvantElaticsearch plugin works only with Elasticsearch on Amazon Web Services (AWS).

The host Linux OS must have pdftotext installed.

The Omeka files folder must contain a directory named `elasticsearch`.

## Installation

To install the AvantElasticsearch plugin, follow these steps:

1. First install and activate the [AvantCommon] plugin
1. Download the latest release from <https://github.com/gsoules/AvantElasticsearch>
1. Unzip `AvantElasticsearch-master.zip` into your Omeka `plugins` folder
1. Rename the folder to `AvantElasticsearch`
1. Activate the plugin from the Omeka `Plugins` page

## Warning

Use this software at your own risk.

##  License

This plugin is published under [GNU/GPL].

This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation; either version 3 of the License, or (at your option) any later
version.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
FOR A PARTICULAR PURPOSE. See the GNU General Public License for more
details.

You should have received a copy of the GNU General Public License along with
this program; if not, write to the Free Software Foundation, Inc.,
51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

## Copyright

-   Created by [gsoules](https://github.com/gsoules)
-   Copyright George Soules, 2019-2020
-   See [LICENSE](https://github.com/gsoules/AvantElasticsearch/blob/master/LICENSE) for more information.

## Credits
The author wishes to thank the Harvard Academic Technology Group at Harvard University, developers of the
[Elasticsearch](https://github.com/Harvard-ATG/omeka-plugin-Elasticsearch) v1.1.1 plugin for Omeka Classic.
It provided helpful insight in how to integrate Elasticsearch with Omeka.


[AvantAdmin]:         avantadmin.md
[AvantCommon]:        avantcommon.md
[AvantCustom]:        avantcustom.md
[AvantDPLA]:          avantdpla.md
[AvantElements]:      avantelements.md
[AvantRelationships]: avantrelationships.md
[AvantSearch]:        avantsearch.md
[AvantS3]:            avants3.md
[AvantZoom]:          avantzoom.md

