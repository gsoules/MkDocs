# Omeka

This page covers Omeka features that Digital Archive administrators commonly need to work with.
See the [Omeka Classic User Manual](https://omeka.org/classic/docs/) for complete documentation on Omeka.

## Terminology
This section explains the meaning of commonly used Omeka terminology.

Item
:   An *item* contains information about an object in your collection including its metadata,
    attached images and documents, and a record of when the item was created and by whom.
    The metadata for an item is stored in *elements.*

Element
:   An *element* is a container for a single metadata value. When you are editing
    an item, you enter data into metadata fields, one for each element.
    Examples of elements are `Title`, `Description`, `Creator`, and `Date`.

Super administrator
:   An Omeka `super administrator` is someone having an Omeka login that allows them to do anything and everything in Omeka.
    Super administrator are the only users with access to the top navigation tabs for Plugins, Appearance, Users, and Settings.
    See the [Omeka Users](https://omeka.org/classic/docs/Admin/Users/) documentation to learn about user levels and access.

## Add a new element
An Omeka installation comes with a predefined set of elements that someone chose to contain all the types
of metadata needed for items in your collection. However, from time to time you may find that you need
a new element to store metadata that your were not previously recording.

Follow these steps to add a new element to your Digital Archive installation.

-   Login to Omeka as a super administrator
-	Click `Items Types` in Omeka's left admin menu
-   Click the `Edit` link below organization's Item Type name
-	On the `Edit Item` page, follow these steps to add an element:
    1.	Choose the `New` radio button at the bottom of the page
    2.  Click the `Add Element button` to expose element name and description fields
    3.	Type the **Element Name** and leave the description blank
    4.	Repeat at Step 2 until done
-	When done adding elements, click the `Save Changes` button
-   See the next section to position the new element among existing elements

## Rename an element
Omeka does not provide a way to rename an element. If you mistype the name when creating a new element, you can simply
delete it and create a new one with the correct name; however, if the element already exists and there are items containing metadata for the element, the only option is to go into the MySQL database and edit the `omeka_elements` table. Find
the element in the table and then change its name in the `name` column. When you go back into Omeka, the element will appear
with its new name. This can be done using [MySQL Workbench](../developer/mysql-workbench.md).

## Arrange element order
You can control the order in which elements appear when you are editing an item.
When editing, the Dublin Core elements appear first, followed by the
other elements. You arrange the order within each of these two groups as explained below.

### Dublin Core elements
-   Login to Omeka as a super administrator
-   Click `Settings` in the top menu bar
-   Click `Elements Sets` in the `Settings` page menu bar
-   Click the `Edit` link under `Dublin Core`
-	Drag the elements into the desired order
-   Click the `Save Changes` button

Below is the order AvantLogic recommends for Dublin Core elements
``` plaintext
Identifier
Title
Type
Subject
Description
Date
Creator
Publisher
Rights
Source
Contributor
Relation
Format
Language
Coverage
```    

### Other elements
-   Login to Omeka as a super administrator
-	Click `Item Types` in the left menu
-   Click the `Edit` link below organization's Item Type name
-	Drag the elements into the desired order
-   Click the `Save Changes` button
