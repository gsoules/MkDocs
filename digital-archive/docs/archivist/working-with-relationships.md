# Working with relationships

---

## Features

Once installed, AvantRelationships extends the Omeka admin and public user interfaces to provide
the ability to add and display relationships. Specifically, the plugin:

-   Adds a `Relationships` menu item in Omeka's admin left menu
-   Adds a `Relationships` button on the admin Item page
-   Adds a `Cover Image` tab on the admin item `Edit` page
-   Displays *Relationship Groups* below an item's metadata on public and admin Item pages
-   Displays a *Visualization Preview* on the public and admin Item pages
-   Adds `Relationships` filter to the bottom of the Omeka `Advanced Search` page

To learn about features provided by AvantRelationships, see the following topics on the
[Digital Archive](http://swhplibrary.net/archive/relationships/) website:

* [Archive Relational Model]
* [Relationships Overview]
* [Viewing Relationships]
* [Adding Relationships]
* [Implicit Relationships]
* [Cover Images]
* [Relationship Types]
* [Relationship Rules]

### Default Rules and Types

To help get you started using AvantRelationships, the installer creates a small set of relationship types and rules.
After installation you can see and edit these by clicking `Relationships` in Omeka's left admin menu. You'll need to
[edit/add/remove rules](http://swhplibrary.net/archive/relationship-rules/) to meet your own needs.
You also want to [edit/add/remove relationship types](http://swhplibrary.net/archive/relationship-types/) in ways that
make sense for your collection.

#### Title Sync Option

The [AvantElements] plugin has a [Title Sync](../plugins/avantelements.md#title-sync-option) option that makes it easy to keep
implicitly related items in sync with each other. If you change the title text in one item, Title Sync will
automatically update the corresponding text in implicitly related items.

Notes:

-   The AvantRelationships plugin only detects an implicit relationships when there is an exact match between the element text in one
    item and the corresponding Dublin Core Title text in another. If the text varies even by a space, the relationship won't be detected.
-   When displaying a creator item, if there are a lot of creation items, the page will display a short list of creation items
    followed by a button that the user can click to see all of the items. The number of items in the short list is controlled
    by the **Max indirect items** option on the AvantRelationships configuration page. If AvantSearch is also installed and activated,
    clicking the button will display all of the related creations as search results in an
    [Image View](http://swhplibrary.net/searching/search-results-image-view/). If AvantSearch is not active,
    clicking the button will display all of the creation items inline on the creator item page.


[Digital Archive]: http://swhplibrary.net/archive
[Digital Archive site]: http://swhplibrary.net/digitalarchive/items/show/9165
[Basic Omeka site]: http://swhplibrary.net/demo/relationships/items/show/9165
[relationships types]: http://swhplibrary.net/digitalarchive/relationships/browse
[Relationships Overview]: http://swhplibrary.net/archive/relationships/
[Viewing Relationships]: http://swhplibrary.net/archive/viewing-relationships/
[Adding Relationships]: http://swhplibrary.net/archive/adding-relationships/
[Implicit Relationships]: http://swhplibrary.net/archive/implicit-relationships/
[Cover Images]: http://swhplibrary.net/archive/cover-images/
[Relationship Types]: http://swhplibrary.net/archive/relationship-types/
[Relationship Rules]: http://swhplibrary.net/archive/relationship-rules/
[Archive Relational Model]: http://swhplibrary.net/archive/digital-relational-model/