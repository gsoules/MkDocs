# The Digital Archive Software

---

The Digital Archive is a [web application](https://en.wikipedia.org/wiki/Web_application) built from a 
combination of free [open-source](https://en.wikipedia.org/wiki/Open-source_software) software and custom 
software developed by George Soules of AvantLogic Corporation for the Southwest Harbor Public Library (SWHPL).
The software implements the [Archive Relational Model](/relationships/archive-relational-model/).
The purpose of this page is to share this resource with other organizations who may be interested
in creating a Digital Archive of their own.

The primary components of the Digital Archive are:

-   Omeka
-   Omeka theme
-   Omeka plugins
-   JavaScript libraries
-   Common Vocabulary Translator
-   Elasticsearch

The sections that follow describe the components listed above.

## Omeka

Omeka (pronounced oh-may-ka) is a Swahili word meaning to display or lay out wares; to speak out; to spread out; to unpack. Omeka is a free, flexible, and open-source web-publishing platform for the display of library, museum, archives, and scholarly collections and exhibitions. Omeka was designed with non-IT specialists in mind, allowing users to focus on content and interpretation rather than programming. To learn more, visit [omeka.org](https://omeka.org/classic/).

Omeka is quick to install and easy to get started with. It stores your data in MySQL which is an open-source relational database management system. The Digital Archive uses MariaDB which is a community-developed fork of MySQL intended to remain free under the GNU GPL free software license since MySQL was acquired by Oracle Corporation.

Note that Omeka uses the term [*item*](/) to refer to a record or entry in its database. Each item represents one entity such as a person, a place, or a thing. An item contains information called [*metadata*](/) that describes the entity. An item can also have an attachment, like a photograph or a PDF file, to supplement the metadata.

#### Strengths and Weaknesses

Omeka is powerful, easy to use, and free; however, its core feature set is too basic to adequately present items in the Digital Archive which are highly relational in nature. Interestingly, popular software solutions, including Omeka, which are commonly used by museums and historical societies, provide few features for establishing and presenting the relationships among items in the database. Consequently, they can’t offer enticing features to help users easily see and discover related items. Furthermore, their presentation of search results tends to be minimal.

Fortunately, Omeka can be extended in two powerful ways. First, because it is open-source, a programmer can change the software to suit the needs of their organization. Second, and a better approach than changing the Omeka software itself, is that programmers can create what are known as “plugins” to extend the capabilities of Omeka. In contrast, proprietary “closed-source” software cannot be modified or extended by those who purchase it.

#### Omeka S

Before moving on to the discussion of Omeka themes and plugins, note that the Digital Archive uses what is now known as Omeka Classic, a term coined by Omeka to distinguish the original Omeka software from a different product called Omeka S. Omeka S addresses some of the shortcomings of Omeka Classic, but still does not provide the capabilities needed for the Digital Archive. Omeka Classic has proven to be a solid platform and therefore remains as the foundation of the Digital Archive.

## Omeka Theme

A theme allows you to customize the look and feel of the public-facing interface of an Omeka website. Like plugins, themes allow an organization to both extend Omeka’s functionality and control the appearance of the website. Omeka comes with a number of themes that you can use as-is or modify. The Digital Archive uses a custom theme called AvantTheme.

## Omeka Plugins

A plugin is a software component that adds features to an existing computer program. Omeka’s rich support for plugins allows a programmer to extend or change Omeka’s features without editing the core Omeka source code. By using plugins, an organization can upgrade to future releases of Omeka Classic without having to reincorporate its custom logic into core source code.

Plugins used by the Digital Archive are listed in the [Software Components](#software-components-used-by-the-digital-archive) section below.

## JavaScript Libraries

JavaScript is a programming language used to make web pages interactive. Alongside HTML and CSS, it is one of the three core technologies used to create web applications. A JavaScript library provides functionality that can be used to extend a web application, similar to the way a plugin can be used to extend Omeka. Two of the most notable libraries that the Digital Archive benefits from are described below.

#### Cytoscape.js

[Cytoscape.js](https://js.cytoscape.org/) is an open-source graph theory library that displays rich, interactive graphics. The Digital Archive uses it to create the [visualization](/user/viewing-related-items/#visualization) graphs that display relationships between the item being viewed and other related items. Each time you view an item in the Digital Archive, the [AvantRelationships](/plugins/avantrelationships/) plugin dynamically generates JavaScript arrays containing definitions of the nodes and edges to be displayed in the graph. Cytoscape interprets the data and displays the visualization.

The layout of graph elements is controlled by Cytoscape extensions. The Dagre layout organizes the graph using a DAG (directed acyclic graph) system. The CoSE Bilkent layout is explained in a paper by U. Dogrusoz, E. Giral, A. Cetintas, A. Civril, and E. Demir, “A Layout Algorithm For Undirected Compound Graphs“, Information Sciences, 179, pp. 980-994, 2009. The AvantRelationships plugin also uses the Concentric layout that is included with Cytoscape. The plugin displays the graph using the Magnific Popup JavaScript library.

#### OpenSeadragon

[OpenSeadragon](https://openseadragon.github.io/) is an open-source, web-based viewer for high-resolution [zoomable images](/administrator/zoomable-images/), implemented in pure JavaScript, for desktop and mobile applications. To be viewed using OpenSeadragon, a large image must be processed into tiles at different scales or tiers. Beginning at a 100% scale, the image is successively scaled in half to produce each tier, until both the width and height of the final tier are at most 256 pixels each. Each tier is further divided into tiles that are at most 256 pixels wide by 256 pixels tall.

SWHPL archivists use a Windows desktop program called [Zoomify](https://openseadragon.github.io/examples/tilesource-zoomify/) to create the tiles for zoomable images. Running the program is a manual step that an archivist must take to create the tiles for an image in the Archive. Once created, the archivist uploads the tiles to the Digital Archive server. When a user views an item, the [AvantCustom](/plugins/avantcustom/) plugin automatically detects if tiles exist for it, and if so, invokes OpenSeadragon to display them.

## Common Vocabulary Translator

The Common Vocabulary Translator (CVT) is a Python program that translates the nearly 15,000
[Nomenclature 4.0](/archivist/common-vocabulary/#nomenclature-40) terms into the simpler
[Common Vocabulary](/archivist/common-vocabulary) terms used in the Digital Archive. It also adds
additional terms to the Common Vocabulary that do not exist in Nomenclature.

## Elasticsearch

[Elasticsearch](https://en.wikipedia.org/wiki/Elasticsearch) is an open-source, distributed search and analytics engine. Since its release in 2010, Elasticsearch has quickly become the most popular search engine. It is used by the Digital Archive for full-text search and for display of the facets in the **_Refine Your Search_** panel. Elasticsearch is the technology that makes it possible for Digital Archive users to
[search one site or all sites](/user/how-to-search/#search-one-site-or-all-sites).

Though Elasticsearch is freely available as open source, the Digital Archive uses the  
[Amazon Elasticsearch Service](https://aws.amazon.com/elasticsearch-service/) to take advantage of the
massive computing power of  
[Amazon Web Services](https://en.wikipedia.org/wiki/Amazon_Web_Services) (AWS).

## Software Components Used By the Digital Archive

The Digital Archive utilizes the following software components (listed by category in alphabetical order). Most are freely available to any organization that wants to use or modify them, but please read the license for each one.

-   Omeka
    -   [MariaDB](https://mariadb.org/) by the MariaDB Foundation
    -   [Omeka Classic](https://omeka.org/classic/) by Roy Rosenzweig Center for History and New Media
    -   [Zend Framework](https://framework.zend.com/) by Zend, Rogue Wave Softwware
-   Omeka plugins
    -   [Archive Repertory](https://github.com/Daniel-KM/Omeka-plugin-ArchiveRepertory) by Daniel Berthereau
    -   [AvantAdmin](/plugins/avantadmin/) by George Soules
    -   [AvantCommon](/plugins/avantcommon/) by George Soules
    -   [AvantCustom](/plugins/avantcustom/) by George Soules
    -   [AvantDpla](http://127.0.0.1:8000/plugins/avantdpla/) by George Soules
    -   [AvantElasticsearch](/plugins/avantelasticsearch/) by George Soules
    -   [AvantElements](/plugins/avantelements/) by George Soules
    -   [AvantHybrid](/plugins/avanthybrid/) by George Soules
    -   [AvantImport](/plugins/avantimport/) by George Soules
    -   [AvantRelationships](/plugins/avantrelationships/) by George Soules
    -   [AvantS3](/plugins/avants3/) by George Soules
    -   [AvantReport](/plugins/avantreport/) by George Soules
    -   [AvantSearch](/plugins/avantsearch/) by George Soules
    -   [AvantVocabulary](/plugins/avantvocabulary/) by George Soules
    -   [AvantZoom](/plugins/avantzoom/) by George Soules
    -   [Bulk Metadata Editor](https://github.com/UCSCLibrary/BulkMetadataEditor) by UC Santa Cruz University Library, Daniel Berthereau
    -   [Geolocation](https://github.com/gsoules/Geolocation) by Roy Rosenzweig Center for History and New Media
    -   [OAI-PMH Repository](https://github.com/gsoules/OaiPmhRepository) by John Flatness
    -   [Simple Vocab](https://omeka.org/classic/docs/Plugins/SimpleVocab/) by Roy Rosenzweig Center for History and New Media
-   Omeka theme
    -   [AvantTheme](https://github.com/gsoules/AvantTheme) by George Soules
-   JavaScript libraries
    -   [CoSE Bilkent](https://github.com/cytoscape/cytoscape.js-cose-bilkent) by the i-Vis group in Bilkent University
    -   [Cytoscape.js](https://js.cytoscape.org/) by the Donnelly Centre at the University of Toronto
    -   [Dagre](https://github.com/cytoscape/cytoscape.js-dagre) by Chris Pettitt
    -   [jQuery](https://jquery.com/) by the JS Foundation
    -   [Magnific Popup](https://github.com/dimsemenov/Magnific-Popup/) by Dmitry Semenov
    -   [OpenSeadragon](https://openseadragon.github.io/) by CodePlex Foundation and OpenSeadragon contributors
    -   [Select2](https://select2.org) by Kevin Brown
-   PHP
    -   [FPDF Library](http://www.fpdf.org/) by Olivier Plathey
-   Python
    -   [Common Vocabulary Translator](https://github.com/gsoules/AvantCommonVocabulary) by George Soules
    -   [PastPerfect Exporter](/technology/pastperfect-exporter/) by George Soules

If you have technology related questions, please send them to gsoules@avantlogic.com.