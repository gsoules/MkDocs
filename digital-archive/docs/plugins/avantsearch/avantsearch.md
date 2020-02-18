# AvantSearch

Provides extended searching and search results capabilities for an Omeka Classic installation.

!!! note
    When this plugin is activated, it dynamically overrides the native Omeka search box with the
    search box used by AvantSearch. When you deactivate the plugin, the Omeka search box returns.

---

## Configuration options

The AvantSearch plugin has these configuration options:

-   [Address Sorting](#address-sorting-option)
-   [Columns](#columns-option)
-   [Detail Layout](#detail-layout-option)
-   [Elasticsearch](#elasticsearch-option)
-   [Integer Sorting](#integer-sorting-option)
-   [Layouts](#layouts-option)
-   [Titles Only](#titles-only-option)

The following sections describe each option in detail.

See also the documentation for [installing AvantSearch](../../../superuser/install-digital-archive/#avantsearch).

---

### Address Sorting option

This option is only supported by [MariaDB](https://mariadb.org/) and MySQL 8.0.
If your server is not running one of these databases, the AvantSearch configuration page will say the option
is not available for your installation. If you want to use this option, contact your web host to ask
about moving to a server that has MariaDB. If your server is running one of the supporting databases and you are
seeing the message that the option is not available for your installation, you'll have to add an element named Address.

Address sorting improves search results by sorting addresses first on the street name and then by the street number as an integer.
Normally addresses are sorted in a database, or in an Excel spreadsheet, as ordinary text where numbers sort before
letters. Furthermore, numbers are normally sorted as text, rather than as integers such that `10` appears before `9`.

Without address sorting:
-   10 Main Street
-   72 Pleasant Lane
-   9 Main Street

With address sorting:
-   9 Main Street
-   10 Main Street
-   72 Pleasant Lane

---

### Columns option

Use the Columns option specify:
-   The order of columns from left to right in search results Table View
-   An alias for an elements name e.g. 'Catalog #' for the Identifier element
-   The width of a column
-   The alignment of column text (left, center, or right)

##### Syntax:

The syntax for each row of the Columns option is
``` plaintex
    <element-name> [ "," <alias>] [ ":" <width> [ "," <alignment>] ] ]
```
Where:

-   `<element-name>` is the name of an Omeka element.
-   `<alias>` is an optional parameter preceded by a comma to provide another name for element e.g. 'ID' for 'Identifier'.
-   `<width>` is an optional parameter preceded by a colon to indicate the width of the element's column in pixels.
-   `<alignment>` is an optional parameter preceded by a comma that can only be specified if `width` is provided. It
specifies the alignment of the column's text as `right`, `center`, or `left`.

#### Column Order:

The order of columns from left to right in search results Table View is determined as follows:
-   The order, first to last, in which you specify elements with the Columns option.
-   For elements that are not specified in the Columns option, the order in which column names appear, top to bottom, and
left to right, in the Detail Layout option.

Note that because of the order precedence above, you cannot have columns appear in a specific order in one layout
and in a different order in another layout. The reason for this restriction is because the content for all columns
is contained in the HTML for the search results Table View; however, only the columns for the selected
layout are visible. When you select another layout, the previous layout's columns are hidden and the new layout's
columns are made visible. This is what allows instantaneous switching between layouts.

Below is an example specification for the Columns option.

``` plaintext
Identifier, Item: 65, right
Title
Type
Subject
Creator
Publisher
Status: 90
```

---

### Detail Layout option

L1 is a special layout referred to as the Detail Layout because it presents a lot of information about an item,
including a thumbnail, in a single column. Use the Detail Layout option to specify the elements which appear in the
Detail layout.

##### Syntax:
Specify each element name on a separate row.

Below is an example specification of the Detail Layout option.

``` plaintext
Identifier
Type
Subject
Creator
Publisher
Date
Place
Address
```

If you prefer to have only one detail column plus the Description column, specify only one row of elements.

---

### Elasticsearch option

Check the **Elasticsearch** checkbox if using [AvantElasticsearch].

---

### Integer Sorting option

The Integer Sorting option lets you specify a list of elements for columns that should be sorted as integers instead
of as text. This option ensures that the data in these column is sorted numerically instead of alphabetically.
For example, an alphabetic sort of `14, 116, 127, 1102` results in `1102, 116, 127, 14` because alphabetically,
the *character sequence* `1102` precedes `14`, `116`, and `127`. Likewise, the characters `14` are greater than the
first two characters in the other three numbers and thus `14` sorts last. The values of elements specified with this
option are converted to integers for sorting purposes.

Below is an example specification of the Integer Sorting option.

``` plaintext
Identifier
Box #
```

Note that you can use the Integer Sorting option for elements with values that only contain integers and also for
elements with values that start with integers, but are followed by text. In that case, the text is ignored and the
sort is performed only on the integer portion of the value.

---

### Layouts option

The Layouts option lets you specify different ways to present search results in Table Vew. The layouts you define
here will appear in the Layout Selector and on the Advanced Search page.

##### Syntax:

The syntax for each row of the Layouts option is
``` plaintex
<layout-id> "," <layout-name> [ "," <admin> [ ":" <column-name> [ "," <column-name>]-   ] ]
```
Where:

-   `<layout-id>` is 'L' followed by an integer e.g. 'L3'. The numbers do not have to be consecutive from layout to layout.
'L1' is reserved for the Detail Layout described in the next section.
-   `<layout-name>` is a short descripion of the layout. It will appear in the Layout Selector list.
-   `<admin>` is an optional instance of the word "admin" (without quotes) to indicate that only a logged in user can
see and choose this layout in the Layout Selector.
-   `<column-name>` is the name of an element that will appear as a column in the layout. Use a comma between column names.

The purpose of the layout Id is to uniquely identify a layout in the query string for Table View page. You can use this
query string as a link on web pages to display search results in a specific layout. The Id ensures that those results
will appear using the correct layout even if you change the layout's name or its position in the Layouts option list.

Below is an example specification of Layouts.

``` plaintext
L1, Summary
L2, Creator/Publisher: Identifier, Title, Creator, Publisher, Date
L3, Type/Subject: Identifier, Title, Subject, Type
L6, Confidential, admin: Identifier, Title, Status, Notes
```

Notes about the example above:
-   Each layout begins with an *Id* and *Name*
-   The fourth row also specifies *'admin'*
-   You don't specify columns for the L1 Layout (described in the next section), but you do specify its *Name*.
-   In the example, the columns for the other layouts always begin with "Identifier, Title" so that users see those
values on every layout. Repeating these columns is a convention, but is not required.

---

### Titles Only option
When this option is checked, radio buttons will appear under the keywords text box on the Advanced Search page to let the user choose
to search in all fields or in titles only. This feature is very helpful for narrowing search results down
to only the most relevant items because titles often contain the most important keywords.

**NOTE:*-   If you want to use this option, but the configuration page says it's not available for your installation, you'll need to add a FULLTEXT
index to the `title` column of the `search_text` table. This is easily done using phpMyAdmin by following these steps:
1. Select the 'search_texts' table
1. Click the Structure tab
1. On the row for the `title` column, click Fulltext among the actions at the far right
1. Click OK on the dialog confirming that you want to add FULLTEXT to the column
1. The `title` column will now appear in the Indexes section showing its type as FULLTEXT (expand the Indexes
section if it's not visible)

---

## Improving Search Results

!!! note ""
    The information in this section is only important when using AvantSearch *without* [AvantElasticsearch].
    AvantElasticsearch uses an entirely different and more effective searching mechanism that is
    independent of the underlying MySQL or MariaDB database.

The AvantSearch plugin will work without any modifications to your database. However, read this section to
learn how you can improve search results by changing just one setting.

Like Omeka's native search, AvantSearch performs keyword searches using the Omeka `search_texts` table.
The Omeka installer creates this table using the MyISAM storage engine. You will get much better results
from keyword searches by changing the table to use the InnoDB storage engine because MyISAM negatively
affects keyword searches in two ways:
 
-   MyISAM uses a very long list of [stopwords](https://dev.mysql.com/doc/refman/5.7/en/fulltext-stopwords.html).
-   MyISAM's default settings ignores keywords of three characters or less (ft_min_word_len).
 
With MyISAM a search for `road+ map+` will ignore `map` and thus return all items containing `road` instead of only
those items containing `road` AND `map`. Additionally, the MyISAM stopword list contains so many words that people
commonly search for that users are often surprised when items don't appear in search results.
 
In contrast, InnoDB has a very short list of stopwords and only ignores keywords that are two characters or less
(innodb_ft_min_token_size). Although you can change the value of ft_min_word_len to 3, this variable
can only be set at the MySQL server level and a server restart is required to change them. If you are
using a shared server, you probably don't have the option to change this value.

Learn how to [change from MyISAM to InnoDB](../../../superuser/install-digital-archive/#change-database-storage-engine).

## Dependencies
The AvantSearch plugin requires that the [AvantCommon] plugin be installed and activated.

## Installation

To install the AvantSearch plugin, follow these steps:

1. First install and activate the [AvantCommon] plugin.
1. Download the latest release from <https://github.com/gsoules/AvantSearch>
1. Unzip `AvantSearch-master.zip` into your Omeka `plugins` folder
1. Rename the folder to `AvantSearch`
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
-   Copyright George Soules, 2016-2020
-   See [LICENSE](https://github.com/gsoules/AvantSearch/blob/master/LICENSE) for more information


## Credits
Inspiration for the Index View search results came from the alphabetized
index and hierarchical list features in the [Daniel-KM / Reference](https://github.com/Daniel-KM/Reference) plugin.


[AvantAdmin]:         ../avantadmin/avantadmin.md
[AvantCommon]:        ../avantcommon/avantcommon.md
[AvantCustom]:        ../avantcustom/avantcustom.md
[AvantDPLA]:          ../avantdpla/avantdpla.md
[AvantElements]:      ../avantelements/avantelements.md
[AvantElasticsearch]: ../avantelasticsearch/avantelasticsearch.md
[AvantRelationships]: ../avantrelationships/avantrelationships.md
[AvantSearch]:        ../avantsearch/avantsearch.md
[AvantS3]:            ../avants3/avants3.md


