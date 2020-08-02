# Using the Vocabulary Editor

The **_Vocabulary Editor _** appears when you click **_Vocabulary Editor _** in the left admin menu.

![Vocabulary editor screenshot](vocabulary-editor-13.jpg)

The vocabulary editor lets you edit the vocabulary terms for these fields:

-   **_Type_**
-   **_Subject_**
-   **_Place_**

To edit vocabulary terms for other fields, use the
[**_Simple Vocab_**](https://omeka.org/classic/docs/Plugins/SimpleVocab/) plugin.

> This page explain how to use the Vocabulary Editor to:

-   [Apply a suggested term](#apply-a-suggested-term)
-   [See which items use a term](#see-which-items-use-a-term)
-   [Choose a common term](#choose-a-common-term)
-   [Add a new vocabulary term](#add-a-new-vocabulary-term)
-   [Edit an existing vocabulary term](#edit-a-vocabulary-term)
-   [Remove a vocabulary term](#remove-a-vocabulary-term)
-   [Apply a suggested term](#apply-a-suggested-term-term)
-   [See all vocabulary terms](#see-all-vocabulary-terms)
-   [See Nomenclature definitions](#see-nomenclature-definitions)

> Meaning of fonts and colors in the Vocabulary Editor

The Vocabulary Editor uses different effects to convey information about terms.
In the screenshot above, all of the terms appear as blue, underlined text to 
indicate that they are common terms; however, you may see other effects as shown below.

![Examples of text coloring](vocabulary-editor-11.jpg)

The table below explains the numbered effects shown above.

 # | Appearance | Meaning
---: | ---: | :---
1 | Red | Unmapped site term
2 | Text inside blue button | A suggested common term (see [Apply a suggested common term](#apply-a-suggested-common-term))
3 | Blue, no underline | Common term with no corresponding Nomenclature term
4 | Blue,  underlined | Common term corresponding to a Nomenclature term
5 | Black | Mapped site term with common term in parentheses.

---

!!! note ""
    The sections that follow assume you are familiar with Digital Archive vocabularies
    and that you know the meaning of *common term*, *site term*, *mapped term*, and *unmapped term*.
    [Learn about vocabularies](/archivist/vocabularies).

## Apply a suggested common term

Sometimes you'll see a blue button like the one below next to a red unmapped site term.

![Suggested term](vocabulary-editor-14.jpg)

The blue button is a special feature that provides you with a suggestion. When you add or edit
an unmapped site term, the Vocabulary Editor looks for a match between the
[leaf term](/archivist/vocabularies/#leaf-term) of the unmapped site term with a corresponding leaf
term in Nomenclature. In this example, the matching leaf term is `Cyanotype`. When there's a match, the blue button appears with a suggestion for a common term to use in
place of the unmapped term. If you like the suggestion, you can click the button,
and then click **_Update_** on the confirmation dialog (shown below), to change the term to use the suggestion
and to update any items that use the term. 

![Suggestion confirmation](vocabulary-editor-12.jpg)

The suggested term is usually appropriate, but not always, so be sure you want to use the term before
you click the **_Update_** button. There is no undo, but if you do update the term by mistake, you can
always [edit the term](#edit-a-vocabulary-term) to change it back to what it was before.

## See which items use a term

To see which items use a specific term, click the number that appears to the left of the term
in the **_Uses_** column. The screenshot below shows that 35 items use the 
term `Image, Art, Drawing`. You could click on `35` to see search results for the 35 items that have
that term as their **_Type_**.

![See which items use a term](vocabulary-editor-7.jpg)

A zero will appear in the **_Uses_** column if no items use that term. Unless you anticipate that archivists
will need the term in the future, [remove it from the vocabulary](#remove-a-vocabulary-term).

## Choose a common term

The next two sections on adding and editing terms require that you choose a term
from the Common Vocabulary. To choose a common term, follow these steps:

1 &ndash; Open the common term chooser dialog
:   To open the dialog, click the **_Choose Common Term_** button in the term's edit form.

2 &ndash; Start typing in the field that says `Enter words here`
:   As you type, terms that match what you enter will appear as suggestions
    as shown below.

    ![Screenshot of common term chooser](vocabulary-editor-4.jpg)

3 &ndash; Click the term you want
:   In the example above, when you click on `Object, Writing, Letter Opener`, the
    chooser dialog will close and that term will appear in the **_Common Term_** field
    of the edit form.

## Add a new vocabulary term

Follow these steps to add a new term:

1 &ndash; Choose the vocabulary kind
:   Select **_Type_**, **_Subject_**, or **_Place_** from the dropdown list at the top of the page.
    The page will update to show the terms currently defined for that kind.

    ![Vocabulary selecter](vocabulary-editor-5.jpg)

2 &ndash; Click the **_Add_** button at the top of the page
:   In this sample above, the button says **_Add Subject_** because the user
    choose the subject vocabulary. Click the button to open
    an edit form as shown below.

    ![Add a new vocabulary term form](vocabulary-editor-1.jpg)

3 &ndash; Fill in the form
:   Do *one* of the following:

    -   Enter a **_Site Term_** *or*
    -   [Choose a **_Common Term_**](#choosing-a-common-term) *or*
    -   Enter a **_Site Term_** *and* choose a **_Common Term_**

4 &ndash; Click the **_Save_** button
:   When you click the **_Save_** button, the term will be added to your
    site's vocabulary and will appear in the corresponding field's dropdown
    list when you add or edit an item.
    For example, when you add a new subject term, the new term will appear in the
    **_Subject_** dropdown.

## Edit a vocabulary term

Follow these steps to change an existing term:    

1 &ndash; Open the edit form for the term
:   Click the pencil icon located to the far right of the term.
    ![Edit an existing vocabulary term](vocabulary-editor-2.jpg) 

2 &ndash; Edit the term
:   Change the **_Site Term_** and/or [choose a **_Common Term_**](#choosing-a-common-term)

    ![Edit an existing vocabulary term](vocabulary-editor-3.jpg) 

3 &ndash; Click the **_Update_** button
:   When you click the **_Update_** button and confirm that you want to make the update:

    -   The term will be changed in your site's vocabulary
    -   It will appear in the corresponding field's dropdown list when you add or edit an item
    -   Every item that uses that term will be updated with the change

## Remove a vocabulary term

To remove an existing term, follow the steps above to edit an existing term,
but then click the red **_Remove_** button in the lower right.
**The button will only appear if the item has zero uses.** To remove a term
that is being used by one or more items, first edit each of those items to
use a different term. When no item is using the term, you can remove it.

## See all vocabulary terms

To see all the terms for a vocabulary, click the **_View Hierarchy_** link located at upper right
of the **_Vocabulary Editor_**. The exact name of the link depends on which vocabulary you are editing.
For example, if you are editing the **_Type_** vocabulary, the link will be **_View Type Hierarchy_**.

![Edit an existing vocabulary term](vocabulary-editor-8.jpg)

The screenshot above shows the first few dozen terms for the **_Type_** vocabulary.
To get back to the Vocabulary Editor, click the **_Return to Vocabulary Editor_** link at upper right.

Searching the page
:   The **_Vocabulary Hierarchy_** page is *very* long. For **_Type_** and **_Subject_** terms, it contains
    thousands of terms. You can use your browser's search feature to find terms on that page. On most
    browsers you can get a search box by pressing **_Ctrl-F_** on Windows, or **_Command-F_** on Mac.

Nomenclature definitions
:   Terms that have a blue hyperlink at the end are from [Nomenclature 4.0](#nomenclature-40).
    Click the link to see that term on the Nomenclature website. See the next section below
    for more information.

Public Page
:    You can share a public link to the **_Vocabulary Hierarchy_** page by editing the URL to remove
    remove `admin`. For example, if the URL is

    `https://swhplibrary.net/digitalarchive/admin/vocabulary/tree?kind=1`

    then the public URL is as shown below (click it to see what the public page looks like)

    [`https://swhplibrary.net/digitalarchive/vocabulary/tree?kind=1`](https://swhplibrary.net/digitalarchive/vocabulary/tree?kind=1)

## See Nomenclature definitions

In the Vocabulary Editor, terms that come from [Nomenclature 4.0](/archivist/vocabularies/#nomenclature-40) appear in blue,
underlined type as shown in the screenshot below.

![Nomenclature term](vocabulary-editor-10.jpg)

Click on one of these terms to see its definition on the
[nomenclature.info](https://www.nomenclature.info) website.
The screenshot below shows the nomenclature.info page for the Nomenclature term `Annual Report`.

![Nomenclature page](vocabulary-editor-9.jpg)

We can now see that the Digital Archive common term for `Annual Report`

```
Document
    Report
        Annual Report
```

is the same as Nomenclature term #13286 for `Annual Report`

``` text
Category 08: Communication Objects
    Documentary Objects
        Administrative Records
            Report
                Administrative Report
                    Annual Report
```

In both cases, the [leaf term](/archivist/vocabularies/#leaf-term) is `Annual Report`, but the parent hierarchies are different.
This information could be useful for someone who has experience working with Nomenclature
and wants to understand how Digital Archive common terms map to Nomenclature terms.
