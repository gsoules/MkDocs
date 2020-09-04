# AvantHybrid

---

The AvantHybrid plugin provides support for items that store a copy of their metadata in the Omeka database,
but have their images hosted on another server.

**WARNING**: The metadata for hybrid items comes from another database and is expected to be treated as
read-only within the Digital Archive. However, the Digital Archive will not prevent an archivist from
editing hybrid items. If an item is updated in the source database, and that database is then synchronized
with the Digital Archive, any changes made to the item using the Digital Archive will be overwritten
by the source data.

## Configuration options
AvantHybrid has these configuration options:

Image URL
:   Use this option to specify the base URL for hybrid images. The URL should end in a forward slash.
    An example appears below.
``` text
https://s3.amazonaws.com/pastperfectonline/images/museum_92/
```

Delete Tables
:   WARNING: Checking this option will cause all hybrid item mappings to be permanently deleted if you uninstall this plugin.


## Dependencies
The AvantHybrid plugin requires that the [AvantCommon] plugin be installed and activated.

## Installation

To install the AvantHybrid plugin, follow these steps:

1. First install and activate the [AvantCommon] plugin.
1. Download the latest release from <https://github.com/gsoules/AvantHybrid>
1. Unzip `AvantHybrid-master.zip` into your Omeka `plugins` folder
1. Rename the folder to `AvantHybrid`
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
-   Copyright George Soules, 2020.
-   See [LICENSE](https://github.com/gsoules/AvantHybrid/blob/master/LICENSE) for more information.


[AvantCommon]:        avantcommon.md