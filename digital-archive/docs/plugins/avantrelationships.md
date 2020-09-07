# AvantRelationships

The AvantRelationships plugin visually displays real-world relationships between items in an Omeka database.
When you view an item, the plugin displays thumbnails and titles of related items. It also displays a graphical
visualization depicting the relationships among items. The user instantly sees how the item fits
in with the rest of the collection and easily discovers related items.

---

!!! note ""
    AvantRelationships requires that each item have a unique identifier. It uses the identifiers to establish the relationship
    between two items. It assumes that you are using the Dublin Core **Identifier** element
    for this purpose. If you are using another element, you must specify it on the AvantCommon configuration page. It also
    assumes use of the Dublin Core **Title** element.

---

## Configuration options

The AvantRelationships plugin has these configuration options:

-   [Custom Relationships](#custom-relationships-option)
-   [Delete Tables](#delete-tables-option)
-   [Max Direct Items](#max-direct-items-option)
-   [Max Indirect Items](#max-indirect-items-option)
-   [Title Relationships](#title-relationships-option)
-   [Visualization Preview](#visualization-preview-option)

The following sections describe each option in detail.

See also the documentation for [installing AvantRelationships](../../../technology/install-digital-archive/#avantrelationships).

---

### Custom Relationships option
This option lets you specify the names of custom callback functions that you write to dynamically create relationships
for the items being viewed (the primary item). The function must create an array of one or more Item objects that are
somehow related to the primary item. These items will appear in their own relationship group at the end of at Item page after all other relationship groups. A relationship to the group will also appear in the visualization.

Custom relationships are one-way from the item being viewed to other items. If you click one of the related
items, its Item page will not display a relationship back to the original item.
 
Each row of the Custom Relationships option specifies one group. The synxtax is:

``` plaintext
<class-name> "," <function-name>
```

Where:

* `<class-name>` is the name of a PHP class in a custom plugin
* `<function-name>` is the name of a public static function in <class-name> 

##### Example use:
```
SomeCustomClass, createCustomRelationshps
```

##### Example custom callback PHP function:

``` php
class SomeCustomClass
{
    public static function createCustomRelationshps(Item $primaryItem, RelatedItemsTree $tree)
    {
        $items = array();
        
        // Put code here to add items to the array that are related to $primaryItem.

        return $tree->createCustomRelationshipsGroup($items, 'Name of Relationship Group');
    }
}
```

---

### Delete Tables option
**WARNING**: Checking this option will cause all relationship database tables and data to be
permanently deleted if you uninstall this plugin. Do not check this box unless you are
certain that in the future you will not be using relationship data that you created
(relationships, types, rules, and cover images) while using this plugin . If you are
just experimenting with the plugin, leave the box unchecked. If you decide not to use
the plugin, check the box, Save Changes, and then uninstall the plugin.

---

### Max Direct Items option
Use this option to specify the number of directly related items that will be listed before displaying a `Show more` message.

---

### Max Indirect Items option
Use this option to specify the number of indirectly related items that will be listed before displaying a `Show more` message.

---

### Title Relationships option
This option lets you specify elements that have an implicit relationship to other items based on the **Title** of those
items. See the description of this option below.

#### Title Relationships
A title relationship is one where the value of an element for one item exactly matches the value of the **Title**
element for another item. For example, if the **Creator** element for a photograph item specifies the name of a
photographer and that photographer's name is used for the **Title** on another item, then there is an implicit
*Created / Created by* relationship between the items.
 
The AvantRelationships configuration page has an option called `Title Relationships` that lets you specify which
elements can have an implicit relationship to items that have a matching Title element value.

In the example above, the plugin displays title relationships in three ways:

-   When viewing one of the photograph items, its Creator text is shown as a hyperlink. Clicking this link
    takes you to the item having the photographer's name as its Title.
-   When viewing the item titled with the photographer's name, photographs created by that photographer
    appear on that page as related items.
-   The title relationships from the creator to his/her creations appear in the Visualization.

The syntax for each row of the Title Relationships option is

``` plaintext
<element-name> ":" <label>
```

Where:

* `<element-name>` is the name of an Omeka element.
* `<label>` specifies the text to describe the relationship in the direction from the titles item to the implicitly
related items. This text appears in the page's related items section and in the visualization.

###### Example:
``` plaintext
Creator: Created
Publisher: Published
```

---

### Visualization Preview option
Specify where the Relationships Visulization Preview should appear. You can have the visualization appear
immediately after metadata elements,or you designate a location, e.g. in the sidebar, by calling the
`show_relationships_visualization` hook in your theme's `items/show.php` page. To not show the visualization,
choose the `Don't show visualization option`.

#### Placement of the Visualization Preview
The preview is a small image of the visualization. When you click on the preview's *Enlarge* link, a full size visualization 
appears in a popup. By default, the AvantRelationships plugin displays the preview immediately after an item's metadata elements
and before item relationship groups. You can have the  preview appear somewhere else such as in the sidebar. To display the graph
at a designated location:

-   On the Configure Plugin page for AvantRelationships, choose `At designated location`*` for the **Visualization Preview** option
-   Call the hook shown below from `/themes/<your-theme-name>/items/show.php` as shown in the example below

```
<div id="secondary">
    <?php fire_plugin_hook('show_relationships_visualization', array('view' => $this, 'item' => $item)); ?>
    ...
</div><!-- end secondary -->
```

If you don't want to show the preview, choose the `Don't show visualization` configuration option.

## Dependencies
The AvantRelationships plugin requires the [AvantCommon] plugin be installed and activated.

AvantRelationships depends on the following open source libraries which are included in
`views/shared/javascripts`. Click the links below to see copyrights and licenses for each.

* [Cytoscape.js](http://js.cytoscape.org/) - graph theory / network library for analysis and visualization
* [cytoscape-panzoom](https://github.com/cytoscape/cytoscape.js-panzoom) - widget that lets the user pan and zoom about a Cytoscape.js graph
* [Dagre](https://github.com/cytoscape/cytoscape.js-dagre) - DAG (directed acyclic graph) for Cytoscape.js
* [CoSE Bilkent](https://github.com/cytoscape/cytoscape.js-cose-bilkent) - layout for Cytoscape.js

## Installation

To install the AvantElements plugin, follow these steps:

1. First install and activate the [AvantCommon] plugin.
1. Download the latest release from <https://github.com/gsoules/AvantRelationships>
1. Unzip `AvantRelationships-master.zip` into your Omeka `plugins` folder
1. Rename the folder to `AvantRelationships`
1. Activate the plugin from the Omeka `Plugins` page

## Uninstalling
You can uninstall AvantRelationships in the usual way; however, by default, the uninstaller will not remove the database tables that store relationship information. This is to protect against accidental deletion of important data. To remove the tables, you must check the **Delete Tables** option on the `Configure Plugin` page, save the change, and then proceed with uninstalling the plugin.

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
-   Copyright George Soules, 2016-2020
-   See [LICENSE](https://github.com/gsoules/AvantRelationships/blob/master/LICENSE) for more information


[AvantAdmin]:         avantadmin.md
[AvantCommon]:        avantcommon.md
[AvantCustom]:        avantcustom.md
[AvantDPLA]:          avantdpla.md
[AvantElements]:      avantelements.md
[AvantRelationships]: avantrelationships.md
[AvantSearch]:        avantsearch.md
[AvantS3]:            avants3.md
[AvantZoom]:          avantzoom.md