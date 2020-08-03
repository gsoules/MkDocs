# Common Vocabulary Translator

The Common Vocabulary Translator (CVT) is a software program that translates the nearly 15,000
[Nomenclature 4.0](/archivist/common-vocabulary/#nomenclature-40) terms into the simpler Common Vocabulary
terms used in the Digital Archive. It also adds additional terms to the Common Vocabulary that do not
exist in Nomenclature. This page explains how the CVT works.

---

!!! note "Advanced Topic"
    This topic is for a person responsible for maintaining the Common Vocabular for multiple
    Digital Archive sites. Use of the Common Vocabulary Translator is not an everyday activity
    and few people have access to the software. **This information is not
    intended for users, archivists, or administrators** though it may be of interest to anyone
    who wants to know how the Common Vocabulary gets created. It does however assume
    familiarity with vocabulary terminology such as *hierarchy* and *leaf*.

## Nomenclature hierarchy

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

## Common Vocabulary hierarchy

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

## Leaf words

In both examples above, the leaf words are the same: `Dressed Stone`, `Buckboard`, and `Negative`.

The CVT preserves Nomenclature leaf words to ensure that they are the same as, and can be
matched with, the same leaf words used in other collection software that uses Nomenclature.

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


## Tail
**Tail** is a CVT term used in the translation rules. The tail consists of Nomenclature's
Primary, Secondary, and Tertiary parts if all three exist. If the term has no Tertiary part,
the tail consists of the Primary and Secondary parts. If the term has no Secondary part,
the tail is just the Primary part. Some higher level terms have no Primary part, but still
 have a leaf which is the Sub Class or Class element. In those cases, the tail is the leaf.

### Translation from Nomenclature to Common Vocabulary

>   Explain how NC gets split into Type and Subject

-   The `Object` term is the only one used as either Type or Subject. That's because collections generally have either an
    actual object such as a hat, or they have a photographs of or documents about an object, for example a photograph of
    a hat worn by a famouse person, or an article about that hat, but the hat itself is not in the collection (or if it is,
    it's separate item). Note that a photograph that serves as a stand-in for an object, should have that object as its Type --
    the Type should not be Photograph. 
-   A few collections contain very large objects such as a boat or a building. Because this is so rare for most collections,
    a full Type hierarchy is not provided for these objects. To accommodate these objects, the Type hierarchy contains:
    -   `Object, Structure`
    -   `Object, Transportation`
    As a boat would have Type `Object, Transportation` and a church bulding would have Type `Object, Structure`. For these items,
    the Subject field can be used to qualify the Type. For example the Subject for the boat could be `Vessels, Boat, Peapod`
    and the Subject for the church could be `Structures, Ceremonial, Church`.
-   If a collection contains many large objects, such as cars, the organization can add Type terms for various kinds of
    automobiles and map them to `Object, Transportation`. For example `Automobile, Electric` and `Automobile, Gasoline`
    could both be mapped to `Object, Transportation`
-   Except for large objects like cars and buildings, in most cases, when an object's Type is specified using the `Object`
    hierarchy, there is no need, and in fact would be bad practice, to also provide a Subject. For example, Type 
    `Object, Clothing, Hat, Bonnet` is self-explanatory, but `Object, Art, Sculpture, Carving` is not. For a carving, the
    Subject could be use to indicate what the carving is of, for example `Nature, Animals, Birds`.

The idea is that any 3D object, whether a physical object in the collection, or a 2D object depicting or about the object,
can easily be cataloged using either the Type and/or Subject `Object` hierarchy.

# Common Vocabulary Translator

Python utility to create Common Vocabulary data from Nomenclature terms.

## Usage

```
>>> build_common_vocabulary.py
```

## Input Files

```
input-nomenclature-sortEn_2020-05-18.csv
input-translations.csv
input-additional-terms.csv
input-previous-digital-archive-vocabulary.csv (if you delete this file, digital-archive-vocabulary.csv replaces it)

```

## Outputs Files

The two output files are automatically uploaded to digitalarchive.us/vocablary

```
digital-archive-vocabulary.csv
digital-archive-diff.csv
```

To get the latest version of Nomenclature 4.0a

1.  [download it as an Excel file](https://www.nomenclature.info/api/download/dataset/nom/nomenclature-sortEn.xlsx)
into the `Python-Common-Facets\data` folder
2.  Open the Excel xlsx file and save it as a CSV file
3.  If you get a `We found a problem` error, click `YES` to recover it
4.  Save the file as `CSV UTF-8`
5   Delete the xlsx file

Note: To compare older and newer versions of Nomenclature using Beyond Compare, use text compare, not table compare.

Examles of the 30 differences from the January 30, 2020 version to the May 18, 2020 version:
-   Renamed `Maple Sugaring Tool` to `Sugaring Tool`
-   Added `Drink Box`
-   Added `Land Grant`
-   Added `Surge Protector`

## Output Files

```
common-facets-natural.csv
common-facets-to-pp.csv
```

### Translation from Nomenclature to Common Vocabulary

The CVT replaces the higher levels (Category, Class, and Sub Class) of the Nomenclature hierarchy with the top-level terms that the Common Vocabulary vocabulary uses for the Digital Archive. The top-level Common Vocabulary terms for the Digital Archive `Type` field are:

-   Document
-   Image
-   Map
-   Object
-   Publication

As shown earlier, the CVT translates:
```
Category 08: Communication Objects
    Documentary Objects
        Graphic Documents
            Photograph
                Negative
```                
to
```
Image, Photograph, Negative
```     

It does this by following rules that tell the CVT to replace `Category 08: Communication Objects, Documentary Objects, Graphic Documents` with `Image` and then append the tail which is `Photograph, Negative`. The next section explains rules.

## Translation Rules

The translation rules are contained in a *translation table* file which is a spreadsheet of rows and columns in CSV format. CSV stands for comma-separated values.

Each row in the translation tables defines one translation rule.

Every rule column is optional except for `Category` and `Translation`.  If the `Category` or `Translation` columns are blank, the CVT ignores the entire row. This allows you to place
blank rows between groups of rules.

The CVT ignores Nomenclature rows having a `level` column value of 1 or 2 because they do no correspond to a leaf term.
A level 1 row only has a category value. A level 2 row has a category and a class.

the CVT processes the Nomenclature terms one at a time to translate them into corresponding Common Vocabulary terms. For each Nomenclature term, the CVT looks for a matching translation rule by starting with the first rule in the translation file, and going to the next rule, until it finds a match.

To find a matching rule, the CVT interprets each rule by comparing the rule's A - F column values, from left to right, against the corresponding values from the Nomenclature row being processed. If *every* non-blank rule column value matches the corresponding Nomenclature row value, the CVT applies the rule, otherwise it skips to the next rule. the CVT only applies one rule to a row.

**Important:** More restrictive rules must occur in the translation file *above* less restrictive rules, otherwise, the CVT will apply a less restrictive rule before it encounters the more restrictive rule. For example, a rule that applies to *any* Nomenclature row having a certain class, must appear *after* a more restrictive rule that applies only to rows of that class that have a specific sub-class or primary value.

### Translation rule columns
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
H | Replace    | A pair of values in double quotes, separated by a comma, specifying before and after values. the CVT applies the replacement to the translated text after peforming the translation.
J |Notes       | Comments (ignored by the CVT)

### Substitution Elements

The `Translation` column of a translation rule must contain one or more of the following substitution elements:

Substitution  | Meaning
--- | ---
`{class}`     | The value of the `Natural_Order_EN_Class` column of the Nomenclature row. Used when the Nomenclature class should be included as-is in the resulting Common Vocabulary term.
`{sub_class}` | The value of the `Natural_Order_EN_Sub_Class` column of the Nomenclature row. Used when the Nomenclature sub class should be included as-is in the resulting Common Vocabulary term.
`{tail}`      | The tail portion (see explanation above) of the Nomenclature term. Used for most rules.
`{leaf}`      | The leaf term (see explanation above) of the Nomenclature term. Used instead of `{tail}` only when the tail value contains more levels of information than are necessary for the resulting Common Vocabulary term.

The `{tail}` and `{leaf}` elements are mutually exclusive and so only one or the other should be used. These two terms
are only ever used at the end of the translation text.

Examples:
```
Transportation|{sub_class}|{tail}
Object|Tools & Equipment|{class}|{tail}
Object|Armaments|{leaf}
```

## Translation Process

The CVT processes one Nomenclature row at a time. When the CVT finds a matching rule for the row, it applies the rule to the row as follows:

1.  It performs the substitutions listed above.

2.  If the rule's `Replace` column is non-blank, the CVT makes the replacement to the translated text. For example, it changes  
`Structures, Commercial, Lodging Facility, Hotel` to `Structures, Commercial, Lodging, Hotel`.

The resulting string becomes the Common Vocabulary term.

`Object|Built Environment|*` becomes ...

`Object|Clothing|{sub_class}|*` becomes ...

`Object|Writing|{leaf}` becomes ...


