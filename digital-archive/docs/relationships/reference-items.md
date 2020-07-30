# Reference Items

## What is a Reference Item

AKA authority items

In the Digital Archive, an item that serves as the stand-in for a person (or boat, house, business etc.)
is called a **Reference Item**. The concept of a reference is central to the Archive Relational Model.
The next section describes the meaning and use of Reference Items and explains why they are so important.

A Reference Item is simply an Omeka item where the type is set to `Reference`. A Reference Item serves as
a stand-in for a real world entity such as a person, place or thing. Information about that entity is in
the item’s metadata which may also be contained in a PDF document attached to the item.

The purpose and importance of Reference items can be explained by an example. Suppose you have two Reference
items about people, one for Robert and another for Theodore. Archivists learn of a woman named Carol, but
know little about her except that she was Robert’s daughter, so they create a Reference item for her that
contains only her name. They also establish a *child of* relationship to Robert’s Reference item. Later,
while researching Theodore, they learn that Carol was his mother and so they establish a *parent of*
relationship from Carol to Theodore.

Now, when you view the Reference Item for Robert, you see his daughter Carol and his grandson Theodore.
Conversely, if you look at Theodore’s Reference Item, you see his mother Carol and his grandfather Robert.
Though Carol’s Reference item is by no means encyclopedic, it glues together grandfather Robert and grandson
Theodore, and it provides a placeholder to put additional information when archivists learn more about
Carol in the future.

The use of Reference Items to glue other items together is what makes the Archive Relational Model so powerful
and so different from other models. Relationships are like the lines that connect the dots in those puzzles
you did as a kid. Until you drew the lines, all you saw was dots and numbers, but once you connected the dots,
you saw a picture! By simply creating a “dot” for Carol and adding relationships, two seemingly unrelated men
became part of a three-generation family tree.


Reference Items serve as the “glue” that binds other items together. A Reference Item is simply an
item that has its **_Type_** metadata field set to `Reference`. [Learn about items and metadata](/).
These special items serve as stand-ins for things in the real world that are typically not part of
a collection, but that tie other items in the collection together via relationships.

The most common use of Reference Items is to provide biographical information about a person, or to
provide historical information about a structure, vessel, business, organization, or event. The *amount*
of information contained in a Reference Item is not always as important as the relationships between
the Reference Item and other items in the collection. As such, a Reference Item
with very little metadata still plays a key role in “connecting the dots” between related items.

To better understand the importance of Reference Items, consider a collection that has three photographs
of the same women. Even if you only knew the woman's name, a Reference Item could be used to tie the
photographs together. In the example below, item 13575 has its **_Type_** set to `Reference` (red arrow).
Items 8930, 8927, and 6751 each have a *depicts* relationship to item 13575 which automatically binds
the four items together such than when you find one of the items, you find them all. Item 13575
itself contains very little information. In a case where you have a lot of information, you could
attach the information to the Reference Item as a PDF file. Learn about [Learn about attachments](/).

![Three photographs of the same women](reference-items-3.jpg)

## How to create a Reference Item

## Cover images for Reference Items

The Cover Image feature allows you to use the image for one item as the representative
image for a Reference Item, but without attaching the image to the Reference Item.
A Reference Item *should not have an image attached to it*, but it can have a PDF
attachment if there is too much information about the item to be contained in the
item's **_Description_** field. The Digital Archive does not enforce this guideline,
but it is a best practice.

The cover image appears in the upper left corner of the Reference Item’s page as though
it were attached with a paperclip. This feature gives some "life" to the Reference Item's
page so that you see the person, not just the PDF file.

![Example of a cover image](reference-items-1.jpg)

### Setting a cover image

To set the cover image for an item:

-   Edit the item
-   Choose the **_Cover Image_** tab
-   In the **_Item_** field, enter the **_Identifer_** number of the item containing the image
-   Click the **_Save Changes_** button

In the screenshots below, the left side shows the **_Cover Image_** tab for item
13579 which appears the example above. The number 11562 has been entered into the
tab's **_Item_** field. The right side is the item page for item 11562. This illustrates
how the image from item 11562 is being used as the cover for item 13579.

![Example of a cover image](reference-items-2.jpg)

    