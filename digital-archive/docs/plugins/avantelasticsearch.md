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

See also the documentation for [installing AvantElasticsearch](../../../technology/install-digital-archive/#avantelasticsearch).

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

The host Linux OS must have pdftotext installed.

The Omeka files folder must contain a directory named `elasticsearch`.

---

!!! warning ""
    This AvantElaticsearch plugin has been tested with AWS Elasticsearch up to v6.8. It might not work with Elasticsearch 7.x, or with AWS Opensearch due to changes in how mapping types work. The plugin relies on the `_doc` mapping. For more information [see this article](https://stackoverflow.com/questions/58824489/where-to-put-include-type-name-in-config-exs).

## Installation

To install the AvantElasticsearch plugin, follow these steps:

1. First install and activate the [AvantCommon] plugin
1. Download the latest release from <https://github.com/gsoules/AvantElasticsearch>
1. Unzip `AvantElasticsearch-master.zip` into your Omeka `plugins` folder
1. Rename the folder to `AvantElasticsearch`
1. Activate the plugin from the Omeka `Plugins` page

## es.ini file
The AvantElasticsearch plugin requires that a file named `es.ini` be located in the root folder
`public_html/digitalarchive` of the installation. The file is not distributed with the plugin,
but you can create it from the sample below. You'll need to edit `es.ini` when you
[install the plugin](/technology/install-digital-archive/#edit-esini).

``` ini
[config]
; These options should only exist on a Digital Archive site used by a developer. They are read by
; AvantElasticsearch to determine if it's okay to create new indexes which is a dangerous operation.
new_shared_index_allowed = true

; Name of the Elasticsearch index that multiple Digital Archive sites share.
shared_index_name = 'devshr'

; Names of Omeka elements that are common among contributors.
common_elements = 'Identifier, Title, Type, Subject, Creator, Date, Place, Rights, Description'

; Names of common elements that can be used to sort shared search results in Table View layouts.
; They are listed in left-to-right order as they will appear in Table View layouts for shared search results.
common_sort_columns = 'Title, Type, Subject, Creator, Date, Place, Rights, Description'

; Layout definitions. The first number is the layout Id which once set, should not be changed since it gets used
; in query strings that serve as permalinks to queries. The number following 'shared_layouts' is just an index and
; has no relationship to the layout Id.
shared_layouts.1 = '1, Details'
shared_layouts.2 = '2, Type / Subject, Identifier, Title, Type, Subject'
shared_layouts.3 = '3, Place / Date, Identifier, Title, Place, Date'
shared_layouts.4 = '4, Creator / Rights, Identifier, Title, Creator, Rights'

; Synonyms for fuzzy searching. The values should be all lowercase.
synonyms.1 = 'rd, road'
synonyms.2 = 'pt, point'
synonyms.3 = 'ave, avenue'
synonyms.4 = 'st, street'
```

The options `common_elements`, `common_sort_columns` and `shared_layouts` control which of these things
are enabled when [searching all sites](/user/how-to-search/#search-one-site-or-all-sites). Think of them as the common denominators among all site. They filter out elements, sort columns, and [search result layouts](/plugins/avantsearch/#layouts-option) that are unique to some individual sites.

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

