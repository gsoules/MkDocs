# Omeka Elements

This page covers Omeka features that Digital Archive administrators commonly need to work with.
See the [Omeka Classic User Manual](https://omeka.org/classic/docs/) for complete documentation on Omeka.

---

## Add a new element
An Omeka installation comes with a predefined set of elements that someone chose to contain 
all the types of metadata needed for items in your collection. At the Omeka level, an element is
a container for a metadata value. In the Digital Archive, elements are referred to as
fields, such as **_Title_**, **_Type_**, or **_Subject_**. Thus, the *elements* in your
Omeka installation correspond to the metadata *fields* associated with items in your collection.

However, from time to time you may find that you need a new element to store metadata that you 
were not previously recording.

Follow these steps to add a new element to your Digital Archive installation.

-   Login to Omeka as an administrator
-	Click **_Item Types_** in Omeka's left admin menu
-   Click the **_Edit_** link below the organization's **_Item Type_** name
-	On the **_Edit Item_** page, follow these steps to add an element:
    1.	Choose the **_New_** radio button at the bottom of the page
    2.  Click the **_Add Element button_** to expose element name and description fields
    3.	Type the **_Element Name_** and leave the description blank
    4.	Repeat from Step 2 until done
-	When done adding elements, click the **_Save Changes_** button
-   [Position the new element](/administrator/omeka-elements/#arrange-element-order) among existing elements

## Rename an element
Omeka does not provide a way to rename an element. If you mistype the name when
creating a new element, you can simply delete it and create a new one with the
correct name; however, if the element already exists and there are items containing
metadata for the element, the only option is to go into the MySQL database and edit
the `omeka_elements` table. Find the element in the table and then change its name
in the **_name_** column. When you go back into Omeka, the element will appear
with its new name. This can be done using [MySQL Workbench](../technology/mysql.md).
If you don't have access to your MySQL database, ask your Digital Archive developer
to rename the element for you.

---

!!! note ""
    You must [rebuild your site's Elasticsearch indexes](/administrator/reindex/) after
    renaming an element If you don't, the old element name will appear on item pages,
    but search results will still show the new name.


## Arrange element order
You can control the order in which elements (i.e., your metatdata fields) appear when you are editing an item.
When editing, the Dublin Core elements appear first, followed by the
other elements. You arrange the order within each of these two groups as explained below.

### Dublin Core elements
-   Login to Omeka as an administrator
-   Click **_Settings_** in the top menu bar
-   Click **_Elements Sets_** in the **_Settings_** page menu bar
-   Click the **_Edit_** link under **_Dublin Core_**
-	Drag the elements into the desired order
-   Click the **_Save Changes_** button

Below is the order AvantLogic recommends for Dublin Core elements
``` text
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
-   Login to Omeka as an administrator
-	Click **_Item Types_** in the left menu
-   Click the **_Edit_** link below the organization's Item Type name
-	Drag the elements into the desired order
-   Click the **_Save Changes_** button

## Make an other element appear with Dublin Core elements
Normally Dublin Core elements appear in a group on the **_Edit Item_** page above a group of other elements.
It is possible however to show an other element within the Dublin Core group, for example to have an
`Accession #` element appear above or below the `Identifier` element. You can't do this yourself, so ask your Digital Archive administrator to do it for you by following these steps:

-   In the `omeka_elements` table, change the other element's `element_set_id` from 3 to 1.
-   Remove the other element from the **_Item Types_** (see Other elements section above).
-   Position the element within the Dublin Core element set (see Dublin Core elements section above).


