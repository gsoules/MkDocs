# AvantAdmin

---

The AvantAdmin plugin customizes Omeka's admin interface and functionality to provide a simpler and more
efficient workflow for archivists. It is intended for Omeka installations that:

-   Do not use Omeka collections
-   Use the same **Item Type** for every item
 
The plugin hides the Omeka **Collections** and **Item Type** options so an archivist does not have
to choose them each time they add a new item. This saves time and ensures that each
new item is added correctly.

AvantAdmin provides the following benefits:

-   Merges the `Dublin Core` and `Item Type Metadata` tabs into a single `Fields` tab
-   Displays the item's image(s) on the Fields tab page
-   Hides the Omeka Item Type dropdown list and assigns the same type to every item
-   Hides the Omeka Collection feature
-   Displays the Item page after a new item is added instead of the Browse Items page
-   Displays Item History on the Item page showing last five users that saved the item
-   Indicates on the Item page if the item is not public
-   Redirects keyword search requests to [AvantSearch]
-   Allows Researcher role to see and search non-public items using the public interface
-   Prevents Research role users from accessing admin pages
-   Shows last 100 modified and recently added items on the Dashboard page
-   Provides a down-for-maintenance feature

## Configuration options
AvantAdmin has these configuration options:

Item Type
:   Specifies the name of the **Item Type** that will be used for every item in the installation.

Maintenance
:   When this option is checked, a `Down for maintenance` page will be displayed to public users to prevent
    them from accessing the site. Logged in users will not be affected.

## Dependencies
The AvantAdmin plugin requires that the [AvantCommon] plugin be installed and activated.

## Installation

To install the AvantAdmin plugin, follow these steps:

1. First install and activate the [AvantCommon] plugin.
1. Download the latest release from <https://github.com/gsoules/AvantAdmin>
1. Unzip `AvantAdmin-master.zip` into your Omeka `plugins` folder
1. Rename the folder to `AvantAdmin`
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
-   See [LICENSE](https://github.com/gsoules/AvantAdmin/blob/master/LICENSE) for more information.


[AvantAdmin]:         ../avantadmin/avantadmin.md
[AvantCommon]:        ../avantcommon/avantcommon.md
[AvantCustom]:        ../avantcustom/avantcustom.md
[AvantDPLA]:          ../avantdpla/avantdpla.md
[AvantElements]:      ../avantelements/avantelements.md
[AvantElasticsearch]: ../avantelasticsearch/avantelasticsearch.md
[AvantRelationships]: ../avantrelationships/avantrelationships.md
[AvantSearch]:        ../avantsearch/avantsearch.md
[AvantS3]:            ../avants3/avants3.md