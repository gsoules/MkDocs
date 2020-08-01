# Getting Started

The Digital Archive provides a new model for sharing local knowledge that is rooted in
time and place. It addresses a shortcoming of popular content management solutions which
isolate database items by not providing archivists with a way to define and establish real-world
relationships that tie collection items together to form stories.

[Relationships](/relationships/getting-started-relationships/) are key in the Digital Archive
[model](/relationships/archive-relational-model/) which is based on two fundamental principles.
The first is that every item in a collection should somehow relate to other items, otherwise it might
not belong in the collection. The second is that users should be able to easily
“connect the dots” by following relationships from one item to another to discover
stories that are of interest to them.

**To get started using the Digital Archive:**

-   Get familiar with the terms and concepts below
-   See [Getting Started for Users](/user/getting-started-user)
-   See [Getting Started for Archivists](/archivist/getting-started-archivist)

---

> Digital Archive terms and concepts

**The terminology below appears throughout the documentation.**
Take a few minutes to read this information so that the rest of the documentation will be easier to understand.

Items & Metadata
:   An **item** represents one *thing* in a Digital Archive collection and all its associated metadata.
    Examples of items are photographs, documents, maps, publications, physical objects.

    **Metadata** is
    information *about* information. For example, the information *in* a photograph is the image
    itself which is a picture of something. The metadata for a photograph is the information *about*
    the image such as the subjects in the picture or the name of the photographer.
    
    Different kinds of metadata are stored in separate
    metadata *fields* such as **_Title_**, **_Type_**, **_Subject_**, and **_Description_**.

    If you have used other kinds of databases, you might be more familiar with the terms *records* and *columns*
    rather than *items* and *fields*. They are the same thing.

    A small collection might have only a few hundred items, whereas a large collection could have tens
    of thousands of items. How easy or difficult it will be for people to find items in a collection
    is affected by the quantity and quality of each item's metadata. Lots of good metadata that is specific to
    each item makes for good search results. Conversely, scant metadata, or metadata that is too broad for the
    item, negatively affects search results.

Type, Subject, and Keywords
:   An item's **type** tells you what kind of *thing* the item is. For example, an item's type might be `photograph`,
    `document`, or `object` (a teacup, for example). An item's **subject** clarifies its type. For example, an item of type `photograph`
    could have the subjects `person` and `boat` to indicate what it is a photograph of.  A subject is not required
    for an item when its type is self-explanatory such as *teacup*. Type and subject terms are defined in
    [vocabularies](/archivist/vocabularies/).
    
    **Keywords** are significant words in an item's **_Title_**, **_Description_** and all other metadata fields.
    There is no separate metadata field for keywords. They are simply the words an archivist chooses to describe an item.

    Each item can have only one type. Typically an item will have one or two subjects and many keywords.
    An archivist's choice of an item's type, subject, and keywords affects how easy it will be for a user to find the
    item when they search the collection.

Image and PDF Attachments
:   An item can have digital images (photographs or scans) and PDF files attached to it. Keywords in the text of
    a searchable PDF file implicitly become part of the item's keyword metadata just as if they appeared in
    the item's **_Description_** or other metadata field. PDF attachments are commonly used to provide the biographical
    or historical information for a Reference item.

    [Learn about attaching files to an item](/archivist/attach-file)

Facets
:   In addition to keyword searching, you can find items by drilling down into a collection
    based on its **_Subject_**, **_Type_**, **_Place_**, and **_Date_** **facets**.
    Facets appears in the **_Refine Your Search_** panel. 
    
    Facets let you find items of interest with just a few mouse clicks. For example, if you are looking for images
    of boats, but don't know what kind of boats are in the collection, you can use the **_Type_** and **_Subject_**
    facets to narrow down search results to `Photographs` of `Vessels`. You can then further narrow down the
    results to something more specific such as `Sailboat`.
    
    [Learn to search using facets](../../user/how-to-search/#search-using-facets)

Reference Items
:   A **Reference Item** is an item that has its type set to `Reference`. These are special items that serve as stand-ins
    for things in the real world that are typically not part of a collection, but that tie other items in the collection
    together via relationships. The most common use of reference items is to provide biographical information about a person,
    and to provide historical information about a structure, vessel, business, organization, or event.

    [Learn about Reference Items](/relationships/reference-items)

Relationships
:   **Relationships** show how items are related to each other. For example, a collection might have three photographs
    of a person, plus a document about that person's life. These items are related because the photographs depict
    the person and the document is about the person in the photographs.

    The Digital Archive displays related items together so that when you see one item, you also see its related items.
    For example, if a search turns up one of the photos of the person, you'll also see the other two photos and the
    document. For this to work, an archivist must establish relationships among the items in the collection.

    [Learn about Relationships](/relationships/getting-started-relationships/)

---

!!! Note ""
    The documentation on this website describes all Digital Archive features, but some features might not be enabled
    on your installation. Which features are available depends on which Digital Archive plugins your site
    administrator has installed. 

---    

This documentation was written by AvantLogic Corporation.  
Please send suggestions for improvement to <gsoules@avantlogic.com>.

  
