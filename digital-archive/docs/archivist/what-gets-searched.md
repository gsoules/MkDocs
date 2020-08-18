
# What Gets Searched

This section explains what gets searched when you type keywords in the search box.
It does not cover [Advanced Search](/user/how-to-search/#advanced-search) which works
differently because it searches specific fields.

## Terminology

To understand what gets searched, you need to understand these terms.

Public and non-Public Items
:   A public item is one that anyone can see. In contrast, only a logged-in Digital Archive user
    can see non-public items. Most items in a collection are public, but an archivist may choose
    to make some items non-public because the item is being worked on and not yet
    ready for public viewing, or because the organization does not have permission to share the item.

Public and Private Metadata Fields
:   Each of an item's metadata fields are designated as either public or private.
    A public field is one that anyone can see in a public item. A private field is one
    that only a logged-in Digital Archive user can see. The text of a PDF file attachment
    is considered public if attached to a public item and private if attached to a
    non-public item.

Visible Items and Fields
:   Which items and fields get searched depends on whether or not the user is allowed to see them.
    A search performed by a logged-in user will search all items and all fields.
    A search performed by someone who is not logged-in will search only the public fields of
    public items. Put another way, all items and fields are visible to a logged-in user, but
    only public fields of public items are visible to a user who is not logged-in.

Searching All Sites

:   The Digital Archive lets you [search one site or all sites](/user/how-to-search/#search-one-site-or-all-sites).
    An All Sites search only searches the public fields of public items. This is true whether or not you are
    logged-in as an archivist. If an archivist needs to search their organization's
    non-public items and private fields, they must switch to searching `This Site` and be logged-in.

## What a keyword search finds

When you type keywords in the search box, the Digital Archive examines:

-   Every item in the collection that is visible to the user
-   The metadata of every one of an item's fields that is visible to the user
-   The text of a visible item's PDF file attachments (the PDF itself must be searchable)

If the keywords exist in one or more of the item's visible metadata fields, that item will show
up as a search result. The words do not need to all exist together in the same field unless
they have been enclosed in double quotes as a phrase.


## Scoring

The searching logic assigns a score to each item that results from a keyword search.
The higher the score, the more relevant the result is. Higher scoring items appear in the
search results above lower scoring items.

When the searched-for keywords appear in the item's **_Title_**, that item's score is increased because the 
**_Title_** field is most relevant for search purposes. The score is also increased, for hits
in the **_Description_** field, though not as much as for the **_Title_** field. To help users find items,
archivists should pay attention to putting keywords in the **_Title_**
and **_Description_** fields.

Hits in items that are of type `Reference` also have their score increased because reference items tend to have
the most relevant information. Also, they are often related to other items. When a user views a
reference item that was returned as a search result, they'll also see all the other items that it
is related to.

If you are logged-in to the Digital Archive,
you'll see each item's score in **_Table View_** when the Details layout is selected.
If you don't want to see the score, your administrator can prevent it from appearing.

## Fuzzy searching

Sometimes the search results will contain items that have metadata that contains words that
are very similar to, but not exactly the same as, the words you type. This is called fuzzy searching.
While this can sometimes produce unwanted results, it's very helpful when you mistype a word or when
you don't know the correct spelling.


