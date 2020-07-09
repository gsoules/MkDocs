# Technologies

---

The Digital Archive is a web application built from a combination of free open-source software and custom software developed for the Southwest Harbor Public Library (SWHPL). The software implements the Archive Relational Model. The purpose of this page is to share our work with other organizations who may be interested in creating a Digital Archive of their own.

The primary components of the Digital Archive are:

    Omeka
    Omeka theme
    Omeka plugins
    JavaScript libraries
    WordPress

The sections that follow describe the components listed above. If you have technology related questions, feel free to contact George Soules by sending email to technology@swhplibrary.net. For questions about Digital Archive content, please contact curator Charlotte R. Morrill via the Contact page.
Omeka

Omeka (pronounced oh-may-ka) is a Swahili word meaning to display or lay out wares; to speak out; to spread out; to unpack. Omeka is a free, flexible, and open-source web-publishing platform for the display of library, museum, archives, and scholarly collections and exhibitions. Omeka was designed with non-IT specialists in mind, allowing users to focus on content and interpretation rather than programming. To learn more, visit omeka.org.

Omeka is quick to install and easy to get started with. It stores your data in MySQL which is an open-source relational database management system. The Digital Archive uses MariaDB which is a community-developed fork of MySQL intended to remain free under the GNU GPL free software license since MySQL was acquired by Oracle Corporation.

Note that Omeka uses the term “item” to refer to a record or entry in its database. Each item represents one entity such as a person, a place, or a thing. An item contains information called metadata that describes the entity. An item can also have an attachment, like a photograph or a PDF file, to supplement the metadata.

Strengths and Weaknesses

Omeka is powerful, easy to use, and free; however, its core feature set is too basic to adequately present items in the Archive which are highly relational in nature. Interestingly, popular software solutions, including Omeka, which are commonly used by museums and historical societies, provide few features for establishing and presenting the relationships among items in the database. Consequently, they can’t offer enticing features to help users easily see and discover related items. Furthermore, their presentation of search results tends to be minimal.

Fortunately, Omeka can be extended in two powerful ways. First, because it is open-source, a programmer can change the software to suit the needs of his or her organization. Second, and a better approach than changing the Omeka software itself, is that programmers can create what are known as “plugins” to extend the capabilities of Omeka. In contrast, proprietary “closed-source” software cannot be modified or extended by those who purchase it.

Omeka S

Before moving on to the discussion of Omeka themes and plugins, note that the Digital Archive uses what is now known as Omeka Classic, a term coined by Omeka to distinguish the original Omeka software from a different product called Omeka S. Omeka S addresses some of the shortcomings of Omeka Classic, but still does not provide the capabilities needed for the Digital Archive. Omeka Classic has proven to be a solid platform and therefore remains as the foundation of the Digital Archive.
Omeka Theme

A theme allows you to customize the look and feel of the public-facing interface of an Omeka website. Like plugins, themes allow an organization to both extend Omeka’s functionality and control the appearance of the website. Omeka comes with a number of themes that you can use as-is or modify. The Digital Archive uses a custom theme called AvantTheme.
Omeka Plugins

A plugin is a software component that adds features to an existing computer program. Omeka’s rich support for plugins allows a programmer to extend or change Omeka’s features without editing the core Omeka source code. By using plugins, an organization can upgrade to future releases of Omeka Classic without having to reincorporate its custom logic into core source code.

Plugins used by the Digital Archive are listed in the Software Components section below.
WordPress

The Digital Archive is actually two websites. One is Omeka and the other is WordPress, a free and open-source content management system.

The page you are reading right now, and other informational pages like it, come from WordPress. Actual data like photographs, maps, and documents, comes from Omeka. You can tell which is which by looking at the URL for any page. The Omeka page URLs always begin with swhplibrary.net/digitalarchive. The WordPress page URLs begin with swhplibrary.net/ followed by the name of the main menu item e.g. swhplibrary.net/home. Here’s another easy way to tell the difference: only the WordPress pages have a search box in the footer. It’s used to search WordPress page content whereas the search box in the header is used to search the Archive.

Using two separate websites best leverages the strengths of the Omeka and WordPress technologies. While Omeka excels at presenting content from a database, it has minimal featrures for creating rich and attractive web pages. Conversely, WordPress has powerful web page creation features, but does not provide database capabilities. By using both technologies, Digital Archive users experience the best possible presentation of information and data, and Digital Archive administrators are able to maintain the web pages and the database using the most appropriate tools for the job.

The above notwithstanding, if you are just creating your own Digital Archive and want to focus your efforts on getting your database online, you can get by with Omeka alone. It’s Simple Pages plugin allows you to create basic web pages for your Omeka website without using another technology like WordPress.
JavaScript Libraries

JavaScript is a programming language used to make web pages interactive. Alongside HTML and CSS, it is one of the three core technologies used to create web applications. A JavaScript library provides functionality that can be used to extend a web application, similar to the way a plugin can be used to extend Omeka. Two of the most notable libraries that the Digital Archive benefits from are described below.

Cytoscape.js

Cytoscape.js is an open-source graph theory library that displays rich, interactive graphics. The Digital Archive uses it to create the visualization graphs that display relationships between the item being viewed and other related items. Each time you view an item in the Digital Archive, the AvantRelationships plugin dynamically generates JavaScript arrays containing definitions of the nodes and edges to be displayed in the graph. Cytoscape interprets the data and displays the visualization.

The layout of graph elements is controlled by Cytoscape extensions. The Dagre layout organizes the graph using a DAG (directed acyclic graph) system. The CoSE Bilkent layout is explained in a paper by U. Dogrusoz, E. Giral, A. Cetintas, A. Civril, and E. Demir, “A Layout Algorithm For Undirected Compound Graphs“, Information Sciences, 179, pp. 980-994, 2009. The AvantRelationships plugin also uses the Concentric layout that is included with Cytoscape. The plugin displays the graph using the Magnific Popup JavaScript library.

OpenSeadragon

OpenSeadragon is an open-source, web-based viewer for high-resolution zoomable images, implemented in pure JavaScript, for desktop and mobile applications. To be viewed using OpenSeadragon, a large image must be processed into tiles at different scales or tiers. Beginning at a 100% scale, the image is successively scaled in half to produce each tier, until both the width and height of the final tier are at most 256 pixels each. Each tier is further divided into tiles that are at most 256 pixels wide by 256 pixels tall.

SWHPL archivists use a Windows desktop program called Zoomify to create the tiles for zoomable images. Running the program is a manual step that an archivist must take to create the tiles for an image in the Archive. Once created, the archivist uploads the tiles to the Digital Archive server. When a user views an item, the AvantCustom plugin automatically detects if tiles exist for it, and if so, invokes OpenSeadragon to display them.
Software Components Used By the Digital Archive

The Digital Archive utilizes the following software components (listed by category in alphabetical order). Most are freely available to any organization that wants to use or modify them, but please read the license for each one.

    Omeka
        MariaDB by the MariaDB Foundation
        Omeka by Roy Rosenzweig Center for History and New Media
        Zend Framework by Zend, Rogue Wave Softwware
    Omeka plugins
        Archive Repertory by Daniel Berthereau, modified by George Soules
        AvantAdmin by George Soules
        AvantCommon by George Soules
        AvantCustom by George Soules
        AvantDpla by George Soules
        AvantElements by George Soules
        AvantRelationships by George Soules
        AvantSearch by George Soules
        AvantZoom by George Soules
        Bulk Metadata Editor by UC Santa Cruz University Library, Daniel Berthereau
        Exhibit Builder by Roy Rosenzweig Center for History and New Media
        Geolocation by Roy Rosenzweig Center for History and New Media, modified by George Soules
        OAI-PMH Repository by John Flatness, modified by George Soules
        Simple Vocab by Roy Rosenzweig Center for History and New Media
    Omeka theme
        AvantTheme by George Soules
    JavaScript libraries
        CoSE Bilkent by the i-Vis group in Bilkent University
        Cytoscape.js by the Donnelly Centre at the University of Toronto
        Dagre by Chris Pettitt
        jQuery by the JS Foundation
        Magnific Popup by Dmitry Semenov
        OpenSeadragon by CodePlex Foundation and OpenSeadragon contributors
        Select2 by https://select2.org
    WordPress
        Custom Sidebars Pro by WPMU DEV
        TablePress by Tobias Bäthge
        Tempera WordPress Theme by Cryout Creations
        WordPress by Matt Mullenweg, Mike Little, and WordPress contributors
        WPForms Lite by WPForms, LLC

Hosting

The Digital Archive website and database reside at Reclaim Hosting, providers of web hosting to educators and institutions.
Credits

The Digital Archive was designed and developed for the Southwest Harbor Public Library by George Soules and Janice Kenyon. Technology funding was provided by the John S. and James L. Knight Foundation with in-kind software engineering services provided by AvantLogic Corporation.