# Glossary

This page provides brief explanations of the terminology used in this documentation
and has links to pages where you can learn more.
Words in **bold** appear elsewhere in this glossary.

---

Administrator
:   An [administrator](/administrator/getting-started-administrator/) is a person who maintains
    their organization's Digital Archive **site**. The **Omeka** documentation refers to an
    administrator as **super user**.

Archivist
:   An [archivist](/archivist/getting-started-archivist/) is a staff member or volunteer who maintain
    a Digital Archive **collection**.

Attachment
:   An [attachment](/archivist/attach-file/#attach-an-image-or-pdf-to-an-item) is a digital
    image file, or a PDF file, that is associated with an **item** such
    that whenever you view the item's **metadata**, you also see the image or PDF.

Archival asset
:   As archival asset is the original digital file from which the web-sized images that are displayed
    by the Digital Archive are derived. The TIFF file produced by a scanner is an archival asset.

AWS
:   AWS is an acronym for [Amazon Web Services](https://en.wikipedia.org/wiki/Amazon_Web_Services),
    a subsidiary of Amazon that provides on-demand cloud computing platforms.

Collection
:   In this documentation, a collection refers to the set of **item**s (images, documents, maps, etc.) in
    an organization's Digital Archive **database**.

Common term
:   A common term is **term** that comes from the **Common Vocabulary**. 

Common Vocabulary
:   The [Common Vocabulary](/archivist/common-vocabulary/) is a set of **vocabulary** **term**s
    organized as a **hierarchy**.

Database
:   A database is a structured set of data, stored and accessed electronically
    from a computer system. The Digital Archive uses **MySQL** as its database.

Developer
:   A developer is a software professional who maintains the Digital Archive software for one or more
    **sites**.

Elasticsearch
:   [Elasticsearch](/administrator/reindex/#what-elasticsearch-indexes-are-used-for)
    is a distributed search and analytics engine that makes fast searching possible.

Element (Omeka)
:   An Omeka element is a container for a single **metadata** value such as title, description,
    type, or subject. In this documentation, element is synonymous with **field**.

Facets
:   Facets are the **_Subject_**, __*Type*__, **_Place_**, and **_Date_**
    sections in the **_Refine Your Search_** panel. They allow users to easily
    narrow down **search results** by clicking on **vocabulary** **term**s in the panel.

Field
:   A field refers to one of an **item**'s **metadata** elements. Examples of fields are
    **_Title_**, **_Description_**, **_Type_**, and **_Subject_**. Field names appear
    in this documentation in **_Small Caps_**. In this documentation, field is synonymous with **element**.
    
    A field is also what you type into when editing an **item**'s **metadata**.

Grid View
:   [**_Grid View_**](/user/viewing-search-results/#grid-view) is a way to view **search results** as a grid of thumbnails.

Guest user
:   A [guest user](/administrator/add-new-user/#guest-user) is a **user** who can see all of the data in a
    **collection** (public and private), but cannot add, edit, or remove an **item**.

Hierarchy
:   A hierarchy is a tiered grouping of related terms that are each unique, but have something in common.
    An example of a hierarchy is the term `Nature, Animals, Birds`. Birds are grouped under animals, and
    animals are grouped under nature.

Index (Elasticsearch)
:   An **Elasticsearch** index is like a table in a database, but is structured in a way that makes
    it possible to search huge volumes of data and get back results instantly.

Index View
:   [Index View](/user/viewing-search-results/#index-view) is a way to view **search results** as an alphabetized list
    of unique values indexed by a specific  **field**.

Item
:   An item represents one *thing* in a Digital Archive **collection** and all its associated **metadata**.
    Examples of items are photographs, documents, maps, publications, and physical objects.

Item page
:   An **item** page is a Digital Archive webpage where you [view an item's metadata](/archivist/items/#view-an-item)
    and any of its image or PDF file **attachment**s.

Item set
:   An [item set](/relationships/kinds-of-relationships/#item-sets) is a two or more **item**s that an
    **archivist** has chosen to group together into a set.

Keyword
:   A keyword is a significant word in an item's **_Title_**, **_Description_** or other **field** that provides
    specific information about the **item** and helps users find items when doing a keyword search.

Left admin menu
:   The left admin menu appears on the left side of every admin page when you are
    [logged in](/archivist/logging-in/) to the Digital Archive as either an **archivist** or **administrator**.
    Admin pages have a beige background.

Lightbox
:   The lightbox is a popup window that appears to display a larger image when you click on an **item**'s
    thumbnail in **search results**.

Metadata
:   Metadata is information about information. For example, the information in a photograph is the image itself
    which is a picture of something. The metadata for a photograph is the information *about* the image such as
    the subjects in the picture or the name of the photographer.

MySQL
:   MySQL is the relational **database** used by **Omeka** to store the **item**s in a **collection**.

Nomenclature 4.0
:   [Nomenclature](/archivist/common-vocabulary/#nomenclature-40) is a structured list of object
    **term**s organized in a classification system for indexing and cataloging collections of human-made objects.
    The latest version is 4.0.

Non-public item
:   A [non-public item](/archivist/special-features-archivist/#non-public-items) is an **item** that only a logged
    in **user** can see. In contrast, any user can see a **public item**.

Omeka
:   [Omeka](/developer/technologies/#omeka) is a web-publishing platform for the display of library, museum,
    archives, and scholarly collections and exhibitions.The [Digital Archive software](/developer/technologies/)
    use Omeka as its foundation.

Organization
:   In this documentation, organization refers to a museum, library, or historical society that is using the
    Digital Archive to make its **collection** available online.

Private field
:   A [private field](/archivist/what-gets-searched/) is a **field** that only a logged in **user** can see.

Pseudo field
:   A pseudo field is one that can be used for searching, or that appears in search results, but is not actually
    a **field**. The pseudo fields are **tags**, [score](/archivist/what-gets-searched/#scoring)
    and [contributor](/user/how-to-search/#contributor-id).

Public field
:   A [public field](/archivist/what-gets-searched/) is a **field** that anyone can see in a **public item**.
    Only a logged in **user** can see a **private field**.

Public item
:   A [public item](/archivist/what-gets-searched/) is an **item** that anyone can see.
    Only a logged in **user** can see a **non-public** item.

Plugin
:   A plugin is a software component that adds features to an existing computer program. The Digital Archive
    plugins add features to **Omeka**.

Reference item
:   A [Reference Item](/relationships/reference-items) is an **Omeka** **item** that relates other items in the **collection** to each other

Relationship
:   A [relationship](/relationships/getting-started-relationships/) is an association between two **items** in a **collection**
    that indicates how the two items are related to each other.

S3
:   S3 stands for [Amazon Simple Storage Service](https://aws.amazon.com/s3/).

Selector
:   A selector is one of the dropdown lists that are grouped together in the selector bar at the top
    of [**_search results_**](/user/viewing-search-results/) pages. The selectors are **_Search_**, **_View_**,
    **_Layout_**, **_Index By_**, **_Sort By_**, **_Per Page_**, and **_Items_**. Not all selectors
    appear together at the same time.

Search results
:   Search results are the list of **item**s that you see when you [search](/user/how-to-search/) a Digital Archive **collection**.

Site
:   A site refers to the Digital Archive software installation and **database** for a single **organization**.

Site term
:   A site term is a **term** that does *not* come from the **Common Vocabulary**. It is specific to an **organization**
    and is found in that organization's **site vocabulary**.

Site vocabulary
:   A site vocabulary is a set of **term**s that are specific to one **organization**'s Digital Archive **site**.

Subject
:   **_Subject_** is a **field** to used to further classify a **Type**. 
    [Learn about **_Type_** and **_Subject_**](/developer/common-vocabulary-translator/#common-vocabulary-type-and-subject).

Super user (Omeka)
:   An Omeka super user is someone with an Omeka login that allows them to do anything and everything in Omeka.
    In this documentation, a super user is referred to as an **administrator**.

Table View
:   [**_Table View_**](/user/viewing-search-results/#table-view) is a way to view **search results** in tabular form.

Tags
:   Tags are words that describe an attribute of an **item**. The
    [Omeka tags feature](https://omeka.org/classic/docs/Content/Tags/) is available in the Digital Archive, but is not
    described in this documentation. The Digital Archive's support for **relationships**, **item sets**, and **hierarchical**
    **vocabularies** make tags less important than in applications that don't have those features.

Term
:   A term is a combination of words in a **vocabulary** that concisely describe or classify something. For example,
    `Image, Photograph, Photographic Print, Cyanotype`is a *single* term that describe a photograph that was printed
     using the cyanotype printing process.

Type
:   **_Type_** is a **field** used to indicate what an item is.
    [Learn about **_Type_** and **_Subject_**](/developer/common-vocabulary-translator/#common-vocabulary-type-and-subject).

Upload
:   Upload refers to the process of copying a file from a personal computer to the Digital Archive which resides on a server.
    You upload a file that you want to **attach** to an **item**.

User
:   A user is anyone that uses the Digital Archive. A user that is logged in like an **archivist** or **administrator** can
    do more than a user who is not logged in.

Zoomable image
:   A zoomable image is a very high resolution image that you can zoom in on to see more detail.

Visualization
:   A [visualization](/user/viewing-related-items/#visualization) (short for data visualization) is a graphical depiction of an **item**'s
    relationships with other items.

Vocabulary
:   A vocabulary is a controlled list of **term**s that **archivist**s use when cataloging **item**s in their **collection**.

Vocabulary Editor
:   The [Vocabulary Editor](/archivist/vocabulary-editor/) lets you work with the **Common Vocabulary** to define
    the set of **common terms** and **site**-specific **term**s that **archivist**s will use when working with **item**s in your **collection**. 