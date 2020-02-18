# AvantS3

Provides [Amazon S3](https://aws.amazon.com/free/storage) storage for archival files.

---

## Configuration options

AvantS3 has these configuration options:

Console
:   S3 management console URL

Bucket
:   S3 bucket name for the Digital Archive

Path
:   Path to database folders

Region
:   AWS server region

Key
:   AWS Access Key Id

Secret
:   AWS Secret Access Key

See also the documentation for [installing AvantS3](../../../superuser/install-digital-archive/#avants3).

---

## Dependencies
The AvantS3 plugin requires that the [AvantElasticsearch] plugin be installed and activated
because AvantElasticsearch contains the AWS/S3 SDK that AvantS3 uses.

## Installation

To install the AvantS3 plugin, follow these steps:

1. First install and activate the [AvantCommon] plugin
1. Download the latest release from <https://github.com/gsoules/AvantS3>
1. Unzip `AvantS3-master.zip` into your Omeka `plugins` folder
1. Rename the folder to `AvantS3`
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
-   See [LICENSE](https://github.com/gsoules/AvantS3/blob/master/LICENSE) for more information.


[AvantAdmin]:         ../avantadmin/avantadmin.md
[AvantCommon]:        ../avantcommon/avantcommon.md
[AvantCustom]:        ../avantcustom/avantcustom.md
[AvantDPLA]:          ../avantdpla/avantdpla.md
[AvantElements]:      ../avantelements/avantelements.md
[AvantElasticsearch]: ../avantelasticsearch/avantelasticsearch.md
[AvantRelationships]: ../avantrelationships/avantrelationships.md
[AvantSearch]:        ../avantsearch/avantsearch.md
[AvantS3]:            ../avants3/avants3.md