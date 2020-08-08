# AvantCommon
 
AvantCommon provides common logic to support the following plugins:  
 
* [AvantAdmin]
* [AvantCustom]
* [AvantDPLA]
* [AvantElasticsearch]
* [AvantElements]
* [AvantRelationships]
* [AvantSearch]
* [AvantS3]

---

## Configuration options

AvantCommon has these configuration options:

-   [Enable Lightbox](#enable-lighbox-option)
-   [Identifer Alias](#identifier-alias-option)
-   [Identifer Element](#identifier-element-option)
-   [Identifer Prefix](#identifier-prefix-option)
-   [Private Elements](#private-elements-option)
-   [Request Image URL](#request-image-url-option)
-   [Unused Elements](#unused-elements-option)

The following sections describe each option in detail.

See also the documentation for [installing AvantCommon](../../../developer/install-digital-archive/#avantcommon).

---

### Enable Lightbox option
The AvantCommon plugin provides support for the Lightbox feature that is used on pages that display thumbnails.
When enabled, the Lightbox feature lets you click on a thumbnail to see it's original-size image in a popup
lightbox.

Check the **Enable Lightbox** checkbox to enable the feature. When this option is unchecked,
clicking on a thumbnail displays the larger image in a separate browser tab.

The Lightbox feature lets you:

-   Click a thumbnail to see a larger image appear in a lightbox
-   See other images on the page by:
    -   Clicking on the current lightbox image to see the next image
    -   Clicking the left and right arrows to see the previous or next image
-   View the item for the image by clicking on the `View Item` link in the caption area
-   Close the lightbox these three ways:
    -   Click on the X in the caption area
    -   Click anywhere on the page outside the lightbox
    -   Press the Esc key

---

### Identifier Alias option
This option lets you specify an alias for the item **Identifier**. Leave this option blank to use the
**Identifier** element's value to display as an item's identifier. If your installation uses a different
element for the public facing identifier value, specify that element as an alias. For example, if you use
a **Catalogue #** element to store a catalogue number such as `2018.123.001`, you could specify
`Catalogue #` as the alias. Note that the alias will appear in search results and as the
identifier for thumbnails.

---

### Identifier Element option
This option lets you specify the element used to uniquely identify an Item. usually this is the
Dublin Core **Identifier** element, but if your installation uses a different element for this
purpose, specify it here. For example: **Object ID**. Note that the identifier element is what
you'll using when establishing relationships using the [AvantRelationships] plugin.

---

### Identifier Prefix option
The prefix is text that will appear before the identifier or alias. You can leave it blank or
provide a value. For example: `Item` or `Catalogue #`.

---

### Private Elements option
Use this option to specify elements that public users should not be able to see or search.
Specify each element name on its on row as shown in the example below.

```
Notes
Status
```
Private element will not:

-   Be visible to public users, but logged in users will see them
-   Be searchable via a public keyword search

For example, you might have elements used to record internal information such as notes and item status that
is meant only for archivists. You can specify `Notes` and `Status` as private elements
to prevent this information from being visible to or searched by the public.

Here are key points regarding private elements:

-   Private elements will not appear as field selections on the Advanced Search page unless
    you are logged in as an administrator.
-   The text of private elements will not be recorded in the `search_texts` table or in hte public
    Elasticsearch index, and therefore will not be searched when performing a public keyword search.
    This is true whether or not you are logged in as an administrator.
-   To search for text in private elements, an archivist can do a field search in those
    fields, either through the public Advanced Search page or using the native Omeka Advanced Search page.
-   If you add an existing element to the private elements list, that element's text will still be
    contained in the `search_texts` table and in the public Elasticsearch index and therefore be found
    via a keyword search. To hide the element's content, you must
    [reindex your Omeka database](https://omeka.org/classic/docs/Admin/Settings/Search_Settings/) to force the `search_texts` table to be rebuilt without the private element text. You will also need to update the public Elasticsearch index.
-   If you uninstall AvantSearch and want to make private elements searchable again, reindex
    your Omeka database and Elasticsearch index as described in the previous bullet.
 
This features solves a problem in Omeka's native search whereby the text of all elements is searched, including
information that is hidden from public users by the [Hide Elements](http://omeka.org/classic/plugins/HideElements/)
plugin. This can produce keyword search results containing items that match the
search criteria, but that don't display the elements that resulted in the hit. For example, the search might
find keywords that appear in an item's hidden **Notes** element, but in no other public elements for that item.
The user then gets a search result that appears to contain none of the keywords they were looking for.

---

### Request Image URL option
Provide the URL of a web page to display when a user requests an image by clicking the
`Request this Image` link at the bottom of the Lightbox. When this value is empty, no
link appears in the Lightbox. The link includes query string parameters for the Item #,
item ID, and image file name so that the linked-to page knows what the request is for.

---

### Unused Elements option
Use this option to specify elements that your installation is not currently using and that
should not appear on the admin Edit page. Specify each element name on its on row as shown
in the example below.

```
Contributor
Relation
Format
Language
Coverage
```

--- 

## Dependencies
AvantCommon depends on the following open source library which is included in the `views/shared/javascripts` folder.
Click the link below to see its copyright and license.

-   [Magnific Popup](https://github.com/dimsemenov/Magnific-Popup/) - lightbox for jQuery that supports the
    [Lightbox feature](#lightbox-feature)

## Installation

1. Download the latest release from <https://github.com/gsoules/AvantCommon>
1. Unzip `AvantCommon-master.zip` into your Omeka `plugins` folder
1. Rename the folder to `AvantCommon`
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

Copyright
---------

-   Created by [gsoules](https://github.com/gsoules)
-   Copyright George Soules, 2016-2020.
-   See [LICENSE](https://github.com/gsoules/AvantCommon/blob/master/LICENSE) for more information.


[AvantAdmin]:         avantadmin.md
[AvantCommon]:        avantcommon.md
[AvantCustom]:        avantcustom.md
[AvantDPLA]:          avantdpla.md
[AvantElasticsearch]: avantelasticsearch.md
[AvantElements]:      avantelements.md
[AvantRelationships]: avantrelationships.md
[AvantSearch]:        avantsearch.md
[AvantS3]:            avants3.md
[AvantZoom]:          avantzoom.md