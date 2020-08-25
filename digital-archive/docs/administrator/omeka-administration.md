# Omeka Administration

Omeka provides features that administrators can use to get the most from the Omeka features of
their Digital Archive site. You can learn how to use most of these features by reading the
[Omeka Classic Documentation](https://omeka.org/classic/docs). This page provides
some additional guidance.

## Add or edit menu items

An administrator can create new menu items and their corresponding pages.
To learn how, read these sections from the Omeka Classic user manual:

-   [Navigation](https://omeka.org/classic/docs/Admin/Appearance/Navigation/)
-   [Simple Pages](https://omeka.org/classic/docs/Plugins/SimplePages/)


## Set the default Home page

The Home page is the one that appears when a visitor first comes to your site.
It is also the page that gets displayed when they click on the banner that appears at the top of every page.

The home page can be an informative page like **_About_** or **_Browse_**, or it can be search results.
To learn how to set the home page, read these sections from the Omeka Classic user manual:

-   [Add a navigation link to the home page](https://omeka.org/classic/docs/Admin/Appearance/Navigation/#add-navigation-links)
-   [Choose the home page](https://omeka.org/classic/docs/Admin/Appearance/Navigation/#choose-a-homepage)

Here are some examples of navigation links you could use for the home page. To use these examples, replace `mysite.net` with the domain name for your site.

```
https://mysite.net/digitalarchive/find?query=&view=4&limit=100
https://mysite.net/digitalarchive/avant/dashboard
https://mysite.net/digitalarchive/find
```

## Add a new user

See the [Add a New User](/administrator/add-new-user/) page in this documentation.

## Work with Omeka elements.

To learn how to add, rename, or reorder Omeka elements, see the [Omeka Elements](/administrator/omeka-elements/)
page in this documentation.

## Make bulk edits

Occasionally you may need to change the values of a large number of metadata fields, for example to
fix a typo or use different wording. When the field is **_Type_**, **_Subject_**, or **_Place_**, you can
easily and safely make bulk changes using the [Vocabulary Editor](/archivist/vocabulary-editor/). For other
fields, you can learn how to use the [Omeka Bulk Metadata Editor](https://omeka.org/classic/plugins/BulkMetadataEditor/) plugin.

** Before using the bulk editor**, be aware of the following:

-   Like any kind of "global replace" feature, bulk editing can result in unintended changes.  
    **There is no undo**, so be sure you know what you are doing.
-   There seems to be a bug in the plugin that causes it to make no changes if you take
    too long to provide all the edit parameters before clicking the **_Apply Edits Now_** button.
    If the changes don't take effect, be a little speedier and try again.
-   For most bulk edits, it's best to *uncheck* the **_Background Job_** at the bottom of the
    **_Bulk Metadata Editor_** page. With the box unchecked, you wait for the changes to be made
    and will know when they are done.
-   [Rebuild your site's Elasticsearch indexes](/administrator/reindex/). If you don't, your bulk
    edit changes will appear on item pages, but search results will still show the old text.
    If you are not comfortable with reindexing, don't make bulk changes, or consult with your Digital
    Archive developer.

---

!!! note "Note"
    If you use the Bulk Editor to change the value of a **_Type_**, **_Subject_**, or **_Place_** field,
    you should use the **_Vocabulary Editor_** to first rebuild your Site Terms table *before* reindexing.
---