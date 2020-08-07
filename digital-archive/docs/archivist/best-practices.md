# Best Practices

##### One man's opinion
The best practices on this page are the recommendations of George Soules.
He has served as a volunteer archivist at the Southwest Harbor Public Library
for six years and holds a degree in Information Sciences from the University of
California. His advice is based on practical experience with what works well and what does not.

## Metadata fields

### Title

The **_Title_** metadata field is more important than any other field because:

-   The **_Title_** field appears everywhere in the user interface &ndash; it's what users see the most
-   Users read the title first to decide if they should view the full item
-   Items with searched-for keywords in their titles *appear highest in search results*

Suggestions:

-   Write titles that concisely describe items in 10 words or less
-   Put non-essential information in other fields, not in the Title field
-   Think of the **_Title_** like ad copy written to catch someone's attention

### Type

Use the most precise **_Type_** field vocabulary terms available. As an example, for an
obituary, use `Document, Announcement, Obituary` instead of just `Document, Announcement`.
If the more precise term is not in your site's vocabulary, don't be lazy &ndash; take
a minute to add it using the [Vocabulary Editor](/archivist/vocabulary-editor/).

Don't be *too* literal when choosing an item's **_Type_**. For example, since you can only put
digital scans and photographs into a database &ndash; because you can't upload an actual teacup
 &ndash; you use *documentary* photographs of objects as *stand-ins* for the real thing.
 The **_Type_** of these items should be the object's type, not `Image, Photograph`.

As an example, suppose your collection contains a teacup that is on display in your
museum. You would photograph the teacup and add the photo to the Digital Archive
as an item of **_Type_**  
`Object, Cup, Teacup`. If you also had a snapshot
of a person drinking from that same teacup, the **_Type_** for the snapshot item *would be*
`Image, Photograph`, but the item would have two subjects: `People` and `Object, Cup, Teacup`.

Note that many organizations have items in their collection that they don't physically
posses. For example, if an archivist borrows, scans, and returns an albumen print,
they would set the **_Type_** of that item to `Image, Photograph, Photographic Print, Albumen Print`
because that's what the item represents.

In summary, choose a **_Type_** that most closely indicates what the item is in the real word.

### Subject

Like types, Subjects should be precise, but not too precise.

The **_Subject_** field is used to *classify* an item, but not uniquely
identify it. For example, the subject of a photograph of a boat can precisely indicate
the kind of boat, but not which boat. For example, the **_Subject_** could be
`Vessels, Ship, Sailing Ship, Schooner` but it should *not* be  
`Vessels, Ship, Sailing Ship, Schooner, Victory Chimes` which is a specific boat.

The limit on how specific subject terms should be has to do with the fact that in cataloging,
classification puts things into groups based on shared attributes such as boats that are all schooners.
The very nature of a group is that it contains multiple things. For a **_Subject_** to be the name
of a specific boat would be to create a group of one which is not classification, but identification.

A guideline for determining when a subject term has gotten as specific as it should be is to consider
what the next level would be. For schooners, would it be their names, their tonnage, the routes
they traveled, the number of masts? If the possibilities of the next level are very broad,
that's probably the cut off point. Another example is the subject `People` which has no lower level
classification. That's because to go one more level would mean having to decide the most important
way to further classify humans. Would it be by gender, ethnicity, religion, age, or height? There's no
clear choice and so `People` is as deep as this subject goes.

In the Digital Archive, archivists use keywords to provide additional specificity. For example, 
a good tile for our schooner would be `Three-masted Windjammer Victory Chimes`. Combined with it's **_Subject_**
`Vessels, Ship, Sailing Ship, Schooner`, this item will show up in results for a keyword search for any
one of these keywords: `ship`, `schooner`, `three mast`, `windjammer`, `victory chimes`. Note that hits
on the last three keywords, which are all in the **_Title_**, will come up higher in search results than hit's
on `ship` or `schooner` which are only in the **_Subject_**. That's because the Digital Archive gives much
more weight to the content of titles than to any other metadata field. It gives the next most weight content
in the **_Description_** field.

In summary, the **_Subject_** field is used to classify items into groups of things
that have something in common, whereas keywords are used to uniquely identify a specific item within a group 

### Date

### Rights



    


TITLE


F.	Date
Unknown birth or death dates – when you know a person is not living, but we don’t know the birth or death date use a “?”:
Gott - Everett Livingston Gott (1875-?)
Gott - Everett Livingston Gott (?-1954)

H.	Creator
The Creator is the “entity primarily responsible for making the content of the resource”. For Article, Document this is the person who wrote the document (e.g. Riebel - Charlotte (Riebel) Morrill). For a photograph, the creator is the person who took the photograph. It is not necessary to specify a creator for Article, Text items with short general descriptions. The Creator field is optional, but when specified, must match exactly the Title of the item for that creator.

-	Define vocabuaries for the site
-	Mangage archival copies of files
-	Only upload web-sized images
-	Define an archival file management scheme
-	Scanning (include scanning resolution tree and other files)

---

## Uploading files

## Vocabulary term

Use unique leaf terms within the same vocabulary.

Don't use comma in Place names unless for hierarchy e.g. `Bangor ME` not `Bangor, ME`

When mapping to a common vocabulary term, you should usually repeat the common vocabulary term
e.g. `Image, Photograph, My custom term` but not always e.g. if you want to elevate your term
e.g. `Carving`.

## Unmapped common term

## Reference Items
A Reference Item should have no image attached to it because its metadata should either
be all text, or some text plus a PDF file attachment. The Digital Archive does not
enforce this, but it is a best practive. See Cover Images
    A Reference Item *should not have an image attached to it*, but it can have a PDF
    attachment.  
    The Digital Archive does not enforce this guideline, but it is a best practice
    because attaching an image to a Reference Item is inconsistent with the 
    [Archive Relational Model](/relationships/archive-relational-model/) which uses the
    *depicts* relationship to associate a Reference Item with all of its images.
	Just because you have only one image now doesn't mean you won't get more later.
---

Metadata appears in fields with names like Title, Description, and Location. Not every item has every metadata field, only the ones that are relevant and for which we have information. Every item has these metadata fields:

    Identifier – Four or five digit number that is unique to that item.
    Title – Brief description of the item. Some items have more than one title. This is common for boats where the name changed over time.
    Type – The kind of real-world object the item represents. Learn about Item Types.
    Subject – What the item is about. Some items have more than one subject. Learn about Subjects.
