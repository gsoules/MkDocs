# Common Vocabulary Translator

The Common Vocabulary Translator (CVT) is a software program that translates the nearly 15,000
[Nomenclature 4.0](/archivist/common-vocabulary/#nomenclature-40) terms into the simpler
[Common Vocabulary](/archivist/common-vocabulary) terms used in the Digital Archive. It also adds
additional terms to the Common Vocabulary that do not exist in Nomenclature.

This page explains:

-   How Nomenclature terms are mapped to Common Vocabular terms
-   How the CVT works

---

!!! note "Advanced Topic"
    This topic is for a person responsible for maintaining the Common Vocabulary for multiple
    Digital Archive sites. Use of the Common Vocabulary Translator is not an everyday activity
    and few people have access to the software. **This information is not
    intended for users, archivists, or administrators** though it may be of interest to anyone
    who wants to know how the Common Vocabulary gets created. It does however assume
    familiarity with [Common Vocabulary terminology](/archivist/common-vocabulary/#terminology).

## Terminology

This section explains terminology that is key to understanding how the CVT works.

### Nomenclature hierarchy

The Nomenclature term hierarchy can be up to six levels deep, though not every term uses all
six levels. The levels are shown below, but note that Nomenclature uses the word *term* to mean
both the entire term and each of the last three levels of the complete term. This can be confusing
which is why this documentation only uses *term* to mean the entire set of words for a complete term.
It refers to the last three levels of a complete Nomenclature term as the Primary, Secondary, and
Tertiary *parts*.

``` text
1  Category
2  Class
3  Sub Class
4  Primary term
5  Secondary term
6  Tertiary term
```    

Here are three examples of Nomenclature terms:

``` text
Category 01: Built Environment Objects
    Building Components
        Construction Materials
            Building Stone
                Dimension Stone
                    Dressed Stone

Category 07: Distribution & Transportation Objects
    Land Transportation T&E
        Animal-Powered Vehicles
            Carriage
                Buckboard

Category 08: Communication Objects
    Documentary Objects
        Graphic Documents
            Photograph
                Negative
```                    

### Common Vocabulary hierarchy

The CVT translates Nomenclature terms into simpler Common Vocabulary terms based on a set
of translation rules that will be explained later. The rules tell the CVT how to translate
the terms shown in the previous section into the terms shown below.

``` text
Object, Building Stone, Dimension Stone, Dressed Stone

Transportation, Carriage, Buckboard

Image, Photograph, Negative
```

As you can see, Common Vocabulary terms are typically much simpler and easier to read than
Nomenclature terms. In fact, approximately 95% of Common Vocabulary terms have four or fewer
levels in their hierarchy. Only about 5% have five levels and none have six.

### Leaf

**Leaf** means the words at the deepest level in a hierarchy. In examples in both sections above,
the leaf words are: `Dressed Stone`, `Buckboard`, and `Negative`.
The CVT preserves Nomenclature leaf words to ensure that they are the same as, and can be
matched with, the same leaf words used in other collection software, like PastPerfect,
that uses Nomenclature.

Nomenclature 4.0 supports leaf words in both *inverted* and *natural order*.
Examples of each follow.

Inverted Order | Natural Order
:--- | :--- 
Negative, Glass Plate | Glass Plate Negative
Negative, Roll File | Roll Film Negative
Negative, Sheet Film | Sheet Film Negative

The Common Vocabulary uses natural order because it's easier to read. 

!!! note "Important"
    Commas are not allowed in Common Vocabulary leaf words because
    comma is reserved as a hierarchy level indicator. This is particularly
    important in place names where comma is  a commonly used separator.
    So for example, in the Common Vocabulary use `Bangor ME` as the leaf,
    not `Bangor, ME`.


### Tail
**Tail** is a CVT term used in the translation rules. The tail consists of a Nomenclature term's
Primary, Secondary, and Tertiary parts, if all three exist. If a term has no Tertiary part,
the tail consists of the Primary and Secondary parts. If a term has no Secondary part,
the tail is just the Primary part. Some higher level terms have no Primary part, but still
have a leaf which is either the Sub Class or Class part. In those cases, the tail and the
leaf are the same.

## How Nomenclature maps to Common Vocabulary 

Nomenclature has thousands of terms for *naming* human-made *objects*, but none for things like
plants or animals, businesses or organizations, or places like towns and villages.
Object terms alone are not sufficient for cataloging many Digital Archive items, especially
[Reference Items](/relationships/reference-items) which serve as stand-ins for real-world entities
like people, boats, and houses.

The CVT adds terms to the Common Vocabulary that don't exist in Nomenclature, and it maps
Nomenclature terms to Common Vocabulary **_Type_** and **_Subject_** terms.

### Common Vocabulary **_Type_** and **_Subject_**

In the Digital Archive, an object name alone is not always sufficient for cataloging an item.
Every item must have a **_Type_**, and unless the type is a physical object that can be
unambiguously described by a Common Vocabulary term, the item must also have a **_Subject_** that further
classifies the **_Type_**. For example, an item with **_Type_** `Object, Cup, Teacup` needs no further
classification, but an item of **_Type_** `Image, Photograph` *must* have a **_Subject_** to
classify the *nature* of the picture. For example, the subject of a photograph could be `People` to
indicate that it's a photo of humans.

The **_Subject_** is *not* used to identify which people are in a photo. That level of specificity
is provided by keywords in the item's **_Title_** and/or **_Description_**. Some subjects convey
significant information about an item, such as `Vessels, Ship, Sailing Ship, Schooner`, but still
stop short of, in this case, identifying the name of the schooner, which again, would be in the item's
**_Title_** and/or **_Description_**.

Though a **_Subject_** is not required for an object item, it can be used to indicate the nature of
the object when the **_Type_** alone is not enough. For example, the **_Type_**
`Object, Art, Sculpture, Carving` names the item as a carving, but does not say what kind. Setting the
item's **_Subject_** to `Natures, Animals, Birds` would provide valuable additional information.

### Which Nomenclature terms map to **_Type_** or **_Subject_**

To satisfy the Digital Archive's requirements for both **_Type_** and **_Subject_**, the CVT maps
the full set of Nomenclature terms into **_Type_** terms, **_Subject_** terms, or both. Here is how
it works in general. Note first that the "Common Vocabulary" is really three vocabularies for 
**_Type_**, **_Subject_**, and **_Place_**.

-   Nomenclature terms for smallish physical objects, like those that might be part of a museum's
    collection, are mapped to the **_Type_** vocabulary *and* to the **_Subject_** vocabulary.
-   Nomenclature terms for very large physical objects like houses, boats, factories, and bridges,
    are mapped to the **_Subject_** vocabulary.
-   Two special objects go into the **_Type_** vocabulary: `Object, Structure` and `Object, Transportation`.
-   Most other Nomenclature terms for objects that are mostly two dimensional, are mapped to the
    **_Type_** vocabulary. These include documents, images, maps, and publications.
-   Additional terms for things like people, animals, businesses, organizations, and events
    are added to the **_Subject_** vocabulary.
-   Terms for the names of towns and villages are added to the **_Place_** vocabulary.

### Rationale for how Nomenclature terms get mapped

Here is the reasoning for the way Nomenclature terms get mapped to the Common Vocabulary
as explained in the previous section.

Museum-size objects
:   Terms for museum-sized objects become both **_Type_** *and* **_Subject_** terms because collections
    generally have either an actual object such as a hat, or they have a photograph of, or documents about,
    an object such as a person. For the hat, the item's **_Type_** would be `Object, Clothing, Hat`
    with no **_Subject_**. For a photograph of a baby, the item's **_Type_** would be
    `Image, Photograph` and the **_Subject_** would be `People`.
    
    The idea is that these object terms can be used for either the **_Type_** or the **_Subject_**
    depending on whether the item actually exists in the collection (**_Type_**)
    or if the item in the collection depicts, or is about, the item (**_Subject_**).
    
    Note that you treat a documentary picture of an object that's in the collection as a stand-in for the actual object
    and thus that item's **_Type_** is the object's type. For example, if your collection contains a teacup,
    the corresponding item **_Type_** is `Object, Cup, Teacup`, not `Image, Photograph`. If you also had a
    snapshot Eleanor Roosevelt drinking from that teacup, the **_Type_** for that photo would be 
    `Image, Photograph` and its two subjects would be `People` and `Object, Cup, Teacup`.

Huge objects    
:   Terms for large physical objects like bridges are mapped to the **_Subject_** vocabulary because
    museums rarely have these kinds of objects in their collections and so there's no sense in having all
    the terms for those objects in the **_Type_** vocabulary. In a case where a collection does actually contain
    something like a church building, the church item's **_Type_** can be set to `Object, Structure` and its **_Subject_**
    can be set to `Structures, Ceremonial, Church`.

    If a collection contains many large objects, such as cars, the organization can use the
    [Vocabulary Editor](/archivist/vocabulary-editor) to add top-level **_Type_** terms for various kinds of
    automobiles, but map them to `Object, Transportation`.   

## Translating Nomenclature to Common Vocabulary

This section explains how the CVT actually performs the mapping from Nomenclature terms
to Common Vocabulary terms. In the diagram below, the black box in the middle represents the
CVT software. The boxes in the top row represent data files that the CVT reads, and the
boxes in the bottom row represent data files that the CVT creates.

![CVT diagram](cvt-1.jpg)

### Translation Rules

The translation rules are contained in a *translation table* file which is a spreadsheet of rows
and columns in CSV format. Each row in the translation tables defines one translation rule.

Every rule column is optional except for `Category` and `Translation`.  If the `Category` or `Translation`
columns are blank, the CVT ignores the entire row. This allows you to place
blank rows between groups of rules.

The CVT ignores Nomenclature rows having a `level` column value of 1 or 2 because they
do not have any leaf words and therefore do not represent a Nomenclature term.
A level 1 row only has a category value. A level 2 row has a category and a class.

The CVT processes the Nomenclature terms one at a time to translate them into corresponding
Common Vocabulary terms. For each Nomenclature term, the CVT looks for a matching translation
rule by starting with the first rule in the translation file, and going to the next rule,
until it finds a match.

To find a matching rule, the CVT interprets each rule by comparing the rule's A - F column values,
from left to right, against the corresponding values from the Nomenclature row being processed.
If *every* non-blank rule column value matches the corresponding Nomenclature row value,
the CVT applies the rule, otherwise it skips to the next rule. the CVT only applies one rule to a row.

**Important:** More restrictive rules must occur in the translation file *above* less restrictive rules,
 otherwise, the CVT will apply a less restrictive rule before it encounters the more restrictive rule.
 For example, a rule that applies to *any* Nomenclature row having a certain class, must appear *after*
 a more restrictive rule that applies only to rows of that class that have a specific sub-class or primary value.

#### Translation rule columns
The table below explains each of the translation rule columns.

 Column | Name | Usage 
 :---: | :--- | :---
A | Category   | Match a value from the Nomenclature `Natural_Order_EN_Category` column
B | Class      | Match a value from the Nomenclature `Natural_Order_EN_Class` column
C | Sub_Class  | Match a value from the Nomenclature `Natural_Order_EN_Sub_Class` column
D | Primary    | Match a value from the Nomenclature `Natural_Order_EN_Primary_Term` column
E | Secondary  | Match a value from the Nomenclature `Natural_Order_EN_Secondary_Term` column
F | Identifier | Match a value from the Nomenclature `Identifier` column. Use this column when the rule should only apply to a single Nomenclature term.
G | Translation| A pattern specifying the Common Vocabulary term. The pattern contains one or more of the substitution elements explained in the next section. 
H | Replace    | Zero or more pair of values in double quotes, separated by a comma, specifying before and after values. the CVT applies the replacement to the translated text after peforming the translation.
J |Notes       | Comments (ignored by the CVT)

As an example, if a rule's **_Replace_** column contained `"Lodging Facility", "Lodging"`,  
the term  `Structures, Commercial, Lodging Facility, Hotel`  
would get changed to `Structures, Commercial, Lodging, Hotel`.

#### Substitution Elements

The **_Translation_** column of a translation rule must contain one or more of the following substitution elements:

Substitution  | Meaning
--- | ---
`{class}`     | The value of the `Natural_Order_EN_Class` column of the Nomenclature row. Used when the Nomenclature class should be included as-is in the resulting Common Vocabulary term.
`{sub_class}` | The value of the `Natural_Order_EN_Sub_Class` column of the Nomenclature row. Used when the Nomenclature sub class should be included as-is in the resulting Common Vocabulary term.
`{tail}`      | The tail portion (see explanation above) of the Nomenclature term. Used for most rules.
`{leaf}`      | The leaf term (see explanation above) of the Nomenclature term. Used instead of `{tail}` only when the tail value contains more levels of information than are necessary for the resulting Common Vocabulary term.

The `{tail}` and `{leaf}` elements are mutually exclusive and so only one or the other should be used. These two terms
are only ever used at the end of the translation text.

Examples of rules in the **_Translation_** column:
```
Transportation|{sub_class}|{tail}
Object|Tools & Equipment|{class}|{tail}
Object|Armaments|{leaf}
```

#### Translation Process

The CVT processes one Nomenclature row at a time. When the CVT finds a matching rule for
a row, it applies the rule to the row as follows:

1.  Perform the substitutions listed in the table above
2.  Makes any replacements specified in the **_Replace_** column
3.  Emits the resulting string as the Common Vocabulary term

## Python Common Vocabulary Translator

The CVT is implemented as a Python program that was developed by
George Soules of AvantLogic Corporation. The source code and data files are
available as open source on [github.com](https://github.com/gsoules/Python-Common-Facets).

##### Usage

```
>>> build_common_vocabulary.py
```

##### Input Files

The program reads these files from the `/data` folder located in the Python script's folder.

```
input-nomenclature-sortEn_2020-05-18.csv
input-translations.csv
input-additional-terms.csv
input-previous-digital-archive-vocabulary.csv

```

##### Outputs Files
The program creates these files in the `/data` folder located in the Python script's folder.  
It also uploads the files to digitalarchive.us/vocabulary

```
digital-archive-vocabulary.csv
digital-archive-diff.csv
```

##### Notes

-   The `digital-archive-diff.csv` will contain update instructions if the CVT found differences
    between `input-previous-digital-archive-vocabulary` and the newly created
    `digital-archive-diff.csv`.
    [Learn how to apply the updates to Digital Archive sites](/developer/site-maintenance/#common-vocabulary-updates).

-   If `input-previous-digital-archive-vocabulary` does not exist as input:

    -   `digital-archive-diff.csv` will be empty because there can be no differences without
    a previous vocabulary to compare to.
    -   The CVT will create a new copy of `input-previous-digital-archive-vocabulary`  
    (the dashed line in the CVT diagram above).

##### Nomenclature data

To get the latest version of Nomenclature 4.0:

1.  [Download it as an Excel file](https://www.nomenclature.info/api/download/dataset/nom/nomenclature-sortEn.xlsx)
    from  
    `https://www.nomenclature.info/api/download/dataset/nom/nomenclature-sortEn.xlsx`
2.  Open the `.xlsx` file and save it as a CSV file
3.  If Excel displays a `We found a problem` error, click `YES` to recover the file
4.  Save the file as `CSV UTF-8`
5.  Delete the `.xlsx` file since it's no longer needed

To compare old and new versions of Nomenclature using B*eyond Compare*, do a text compare, not a table compare.
