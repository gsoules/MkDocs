
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

## What a keyword search finds

When you type keywords in the search box, the Digital Archive examines:

-   Every item in the collection that is visible to the user
-   The metadata of every one of an item's fields that is visible to the user
-   The text of a visible item's PDF file attachments (the PDF itself must be searchable)

If the keywords exist in one or more of the item's visible metadata fields, that item will show
up as a search result. The words do not need to all exist together in the same field unless
they have been enclosed in double quotes as a phrase.


## Relevance

The searching logic assigns a score to each item that results from a *keyword* search.
The higher the score, the more relevant the result. Higher scoring items appear in the
search results above lower scoring items.

Search results will be returned in order from most to least relevant, but only for keyword searches on 'All fields' with the 'All words' or 'Boolean' condition. Relevancy searching is not supported for 'Titles only', the 'Contains' condition, or when searching by fields, year range, or tags.

The ranking of results is based on the following from highest to lowest:

- The keywords appear in the Title field *and* the item's type is 'Reference'
- The keywords appear in the Title field.
- The item's type is 'Reference'
- The keywords appear in the Description field
- The keywords appear in other fields, but not in the Title or Description

