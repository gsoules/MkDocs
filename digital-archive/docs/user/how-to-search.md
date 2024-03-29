# How to Search

You can search the Digital Archive in three ways:

- Type **keywords** into the search box
- Click **facets** in the **_Refine Your Search_** panel
- Use the **_Advanced Search_** page

[Learn about what gets searched](/archivist/what-gets-searched)

## Search using keywords

To search using keywords, type words in the search box that displays in the upper right of
every Digital Archive page. Click the magnifying glass icon or press `Enter` on your keyboard to start the search.

![Quick Search Box](how-to-search-3.jpg)

The search results will show items that contain *all* of the keywords that you entered.
You can search for items containing *any* of the keywords by using special characters.
See the [Special Characters Used for Searching](#special-characters-used-for-searching)
section below to learn how.

!!! Note ""
    **TIP**: If you know an item's **_Identifier_** number, you can type the number into the search box to go
    directly to the page for that item. This only works when searching the site you are on. When
    searching All Sites, you'll get search results for items having that number in their metadata.

As you type into the search box, suggestions will appear as shown below. The suggestions come from the titles
of items that contain the same or similar keywords as what you type. For instance, suggestions containing
`jordan` appear because it is similar to `jordon`. If no suggestions appear, or there are none that you like,
it only means that no *titles* match what you typed &ndash; it does not mean there is no matching content,
so always click the magnifying glass icon or press `Enter` to do a search. In this
example, the actual search for `jordon` returned 547 results.

![Quick Search Box](how-to-search-14.jpg)

The primary purpose of the search suggestions is to help you discover things that you might not know about.
They are also very useful when you are not sure how to spell something. In the example above, the user was
looking for items about Jordan Pond. Even though they misspelled `Jordan` the suggestions reveal that not
only are there items about Jordan Pond, but about people, houses, and roads with that name.

## Search one site or all sites

You can search just the site you are on (for example, only search the Southwest Harbor Public Library) or
you can search all sites that are sharing their collections with each other. To choose which sites to search
use the **_Search_** selector that appears in the options bar at the top of
the search results page.

-   **To search all sites**, use the **_Search_** selector to choose `All Sites`

-   **To search just the site you're on**,  use the **_Search_** selector to choose `This Site`

![Searching selector options](how-to-search-11.jpg)

Learn how this works by reading about [Elasticsearch indexes](/administrator/reindex/#what-elasticsearch-indexes-are-used-for).

## Search using facets

Facets allow you to narrow down search results that you are viewing, or to narrow down all of the
items in the collection to just the items you are interested in.

!!! Note ""
    **TIP**: To see all of the items in a collection, click on the magnifying glass icon next to the search box
    *with no keywords entered*. You can then use facets to narrow down the entire collection.

 Facets appear in the **_Refine Your Search_** panel. They are: **_Subject_**, __*Type*__,
 **_Place_**, and **_Date_**. When searching all sites, the **_Contributor_** facet also appears. 

Facets let you find items of interest with just a few mouse clicks. For example, if you are looking for pictures
of cottages, you can use the **_Type_** and **_Subject_** facets to narrow search results to `Images` of `Cottages`.
You could then further narrow down the results to only items from a specific place such as `Seal Harbor`.
You can also use facets in combination with keyword or advanced searching to limit the results to
items having specific metadata. The example below shows a search using the **_Type_**, **_Subject_**, and
**_Place_** facets plus the keyword `rockefeller`.

![facet search](how-to-search-2.jpg)

As you click on facets in the **_Refine Your Search_** panel, the contents of the panel shrink down to only
show facets that apply to the current search results. You can remove a facet by clicking the `X` next to its name
in the panel or in the corresponding blue boxes that appear above the search results.

## Advanced Search

When you need to narrow search results to something more specific than is possible using either keywords
or facets, click on the `Advanced Search` link under the search box to go
to the **_Advanced Search_** page. That page lets you specify search criteria for individual 
metadata fields. You can also use it to specify an inclusive range of years.

![advanced search](how-to-search-4.jpg)

Typically, you use advanced search to either limit results to items containing metadata for a specific
field, or you use it to exclude items that do not contain certain metadata.

The example below shows a search for items that have `structure` in their **_Subject_** field, but *not*
`commercial`. In other words, non-commercial structures. In this example, the items must also be either documents or
publications, that is, no images or objects. Futhermore, the **_Title_** field must *not* contain
the phrase `annual report`. Finally, items must have a year value before 1900 in the **_Date_** field.

![advanced search](how-to-search-6.jpg)

The screenshot below shows the results of the Advanced Search above. Notice that no facets are selected, but
you could still use them. For example, you could choose the `Southwest Harbor` facet to narrow the results
to display only items from that town that meet the criteria above.

![advanced search](how-to-search-5.jpg)

### Special characters used for searching

The right-side of the **_Advanced Search_** page lists special characters you can use when searching.
You can also use this syntax in the search box that displays in the upper right of every page.


![advanced search](how-to-search-8.jpg)

The special characters are especially useful when you want to circumvent the fact that,
by default, keyword search results display items containing *all* of the keywords you specify. For example, a
search for `islesford frenchboro` returns the six items that have *both* `islesford` *AND* `frenchboro` in their
metadata.

![advanced search](how-to-search-9.jpg)
![advanced search](how-to-search-10.jpg)

When you separate the words by the special `|` character to signify *OR*, the search returns the 433
items that contain either or both words. The addition of `-postcard` eliminates items that contain that keyword.

![advanced search](how-to-search-7.jpg)

## Site statistics

Site statistics show the contributions of all organizations that are sharing their collections
with each other. To see them, click the **_View site statistics_** link that is located above
the **_Search Tips_** box on the **_Advanced Search_** page.

![advanced search](how-to-search-12.jpg)

The rows are sorted by the total *weight* of the items in each organization's Digital Archive
collection. An item's weight reflects the amount of information it provides.

The weight of a single item is calculated as follows:

-   The item itself &ndash; its metadata &ndash; is worth 1 point
-   Each of the item's [file attachments](/archivist/attach-file/) (image, document, audio, video) is worth 1 point
-   Each of the item's [relationships](/archivist/add-relationship/) is worth &frac12; point

Relationships get a &frac12; point because every relationship is shared by two items.

Here are a few examples of weight calculations:

-   An item with just metadata and no attachments and no relationships has a weight of 1
-   An item with one image attached has a weight of 2
-   An item with 4 images, 1 PDF, and 2 relationships has a weight of 7 (1 + 4 + 1 + &frac12; + &frac12; )

*The screenshot above was taken on August 18, 2020.*

##### Contributor ID

The ID column shows the abbreviation used for each contributing organization. You can use this value
on the [Advanced Search page](#advanced-search) to:

-   Limit searches to only specific organizations
-   Exclude specific organizations from searches

For example, the Advanced Search shown below would *exclude* the three libraries listed in the table above from the search.

![advanced search](how-to-search-13.jpg)

To search *only* those three libraries, change the condition to `(swhpl|nehl|jml)`.

The **_Contributor_** pseudo field only appears in the **_Fields_** dropdown when
you are searching All Sites. It won't be listed when searching This Site.

---
