# Searching

---

## Differences from Omeka

AvantSearch completely overrides Omeka's public search features. It provides its own
[Advanced Search](#tadvanced-search-page) page
and presents search results in a wide variety of ways. It does not affect Omeka's admin search.
The table below highlights the differences between AvantSearch and Omeka's native search.

Feature | AvantSearch | Omeka Search
--------|------------ | ------------
[Quick search](#quick-search) |  **Yes** - Feature | No
[Simple search for All Words](#simple-search) |  **Yes** - Feature | No
[Search in Titles only](#titles-only-option) | **Yes** - Advanced Search page option | No
[Search only items with images or files](#advanced-search-page) | **Yes** - Advanced Search page option | No
[Date range search](#advanced-search-page) | **Yes** - Advanced Search page option | No
[User can specify number of results](#advanced-search-page) | **Yes** - Advanced Search page option | No
[Tabular results](#table-view) | **Yes** - Feature | No
[Custom Results Layouts](#table-view-custom-layouts) | **Yes** - Congfiguration option | No
[Image View](#image-view) | **Yes** - Feature | No
[Index View](#index-view) | **Yes** - Congfiguration option| No
[Relationships View](#relationships-view-option) | **Yes** - Congfiguration option | No
[Integer sorting](#integer-sorting-option) | **Yes** - Congfiguration option | No
[Address sorting](#address-sorting-option) | **Yes** - Congfiguration option | No
[Lightbox](#lightbox) | **Yes** - Feature | No
Search by File, Collection, Featured | No | Yes

### Quick Search
Quick Search is a feature of Simple Search that allows you to immediately go to the page for an item by typing the
item's Identifier value in the simple search box. This is much faster than getting back search results for every item
that contains that value and then having to locate and click on the item of interest.

### Simple Search
The AvantSearch version of simple search improves on the native Omeka simple search by only returning results that
contain *all* of the matching keywords instead of any of the keywords. Items that contain some, but not all of the
keywords will not appear in the results. Searching for all keywords tends to provide much more relevant results.
If you need to search for any of the keywords, you can enter the keywords
on the Advanced Search page and choose the Boolean condition.

## Search Results Views
One of the most powerful features of AvantSearch is its ability to display search results in many different ways
which you can customize to meet your needs. In addition to the Index View presentation described later,
the Table View lets you specify any number of different layouts to display results in rows and sortable columns.
The screen shots that follow show the same AvantSearch results in three different Table View layouts.

### Table View

#### Table View Detail Layout
The Detail Layout provides a compact presentation of key information about an item including a thumbnail image.
You specify which elements appear in the two columns to the right of the thumbnail. The item's description
automatically appears in the third column. The screen shot below is truncated after the first three results.

![Summary Layout Example](search-1.jpg)

---

#### Table View Custom Layouts
This is an example of a custom layout showing the item's Type and Subject elements. The red triangle next to 'Type'
in the header indicates that the results are sorted ascending by Type. The screen shot below is truncated after the first 10 results.

![Custom Layout Example](search-2.jpg)

---

This is another example of a custom layout, but this one shows the item's Creator and Publisher elements.
Note the asterisk on item 2636. When you are logged in as an administrator, the astersisk indicates that the item
is not public. When not logged in, the item does not appear in the results. You can also define layouts that can
only be chosen when logged in. These layout can be used to show data that is normally hidden from public users.
The screen shot below is truncated after the first 10 results.

![Custom Layout Example](search-3.jpg)

### Image View
Image View displays search results as a grid of thumbnails. It's a more compact way to view results when the image is
most important for identifying items of interest. The screen shot below is truncated after the first 10 results.

![Image View Example](search-4.jpg)

### Index View
Index View displays information like the index in a book. It consolidates values into unique groups having the same
value. The screen shot below is truncated midway through the B's.

When the index field contains hierarchical data, Index View shows only the leaf (lowest level) values in the
hierarchhy. For non-hierarchical data, Index View shows the entire value. The data is considered to be
hierarchical only if the index field element is specified using the Hierarchies option, 
otherwise Index View displays it as flat data.

![Index View Example](search-5.jpg)

## Lightbox
Both the Table View Detail Layout and the Image View display thumbnails for an item's image if it has one. If the item
has no image, a placeholder image is displayed. When you click on a thumbnail, the AvantSearch plugin displays a large
version of the image. You can have the image display in a popup by using the
[Lightbox feature](../avantcommon/avantcommon.md#lightbox-feature) of the
[AvantCommon] plugin.

![Lightbox Example](search-8.jpg)

## Advanced Search Page
AvantSearch provides its own Advanced Search page. You access this page by either clicking on the Advanced Search
link that appears below the simple search box in the header of every page, or by clicking the Modify Search button
that appears on search result pages.

The screen shot below shows the search conditions that were
specified to generate the Table View Custom Layout - Type / Subject screen shot shown earlier.

![Advanced Search Page](search-7.jpg)

## Date Range Feature
When AvantCommon is configured to provide Start and End years, year start and end text boxes will appear as
filters at the bottom of the Advanced Search page. A user can provide values for both the start and end years to
limit search results to items in that range inclusive. For example if you specify 1900 for the start year and
1940 for end year, search will find items with start year greater than or equal to 1900 and less than or equal to 1940.
If you only provide a value for the start year, the search will find items where the start year is that date
or more recent. If you only provide a value for the end year, the filter will find items where the end year is that
date or older.

