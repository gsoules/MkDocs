# Common Facet Translator

Python utility to create Common Facet data from Nomenclature terms.

## Usage

```
>>> build_common_facets.py
```

## Input Files

```
nomenclature-sortEn2020-01-30.csv
nomenclature-translations.csv
nomenclature-additions.csv
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

## The Common Facet Translator (CFT)

The Common Facet Translator (CFT) translates the nearly 15,000 [Nomenclature 4.0](https://www.nomenclature.info/apropos-about.app?lang=en) terms into a simpler Common Facet terms used in the Digital Archive. The hierarchy for a single Nomenclature can be up to six levels deep, though not every term uses all six levels. The levels are:

1.  Category
1.  Class
1.  Sub Class
1.  Primary term
1.  Secondary term
1.  Tertiary term

Here are three examples of Nomenclature terms:

```
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

The Common Facet Translator (CFT) translates Nomenclature terms into a simpler Common Facet terms strings based on a set of translation rules that will be explained later. The rules tell the CFT how to translate the hierarchy shown above into the strings shown below.

```
Object, Built Environment, Building Stone, Dimension Stone, Dressed Stone

Transportation, Carriage, Buckboard

Image, Photograph, Negative
```

### Hierarchy Terminology

#### Leaf
The deepest element in any hierarchy is called the *leaf term*. In Nomenclature, every leaf term is unique which makes it possible to determine the full hierarchy from just the leaf term. In the examples above, the leaf terms are `Dressed Stone`, `Buckboard`, and `Negative`.

To ensure that each leaf term is unique, Nomenclature add words to leaf terms to distinguish them from other leaf terms. For example, in addition to the leaf term `Negative`, there are leaf terms for `Glass Plate Negative`, `Roll Film Negative`, and `Sheet Film Negative`.

The CFT preserves Nomenclature leaf terms -- it never translates them -- to ensure that they are the same as and can be
matched with the same terms used in other applications such as PastPerfect.

Nomenclature 4.0 supports leaf terms in both *inverted* and *natural order*. Examples of inverted order are `Negative, Glass Plate`, `Negative, Roll File`, and `Negative, Sheet Film`. The CFT uses the natural order terms when generating Common Facet terms for the Digital Archive.

#### Tail
To convert Nomenclature terms to Common Facet terms, the CFT puts special emphasis on the *tail* of the hierarchy. The tail consists of the Primary, Secondary, and Tertiarty elements if all three exist. If the term has no Tertiary element, the tail consists of the Primary and Secondary elements. If the term has no Secondary element, the tail is just the Primary element. Some higher level terms have no Primary element, but still have a leaf term which is the Sub Class or Class element. In those cases, the tail is the leaf term.

### Translation from Nomenclature to Common Facets

The CFT replaces the higher levels (Category, Class, and Sub Class) of the Nomenclature hierarchy with the top-level terms that the Common Facet vocabulary uses for the Digital Archive. The top-level Common Facet terms for the Digital Archive `Type` field are:

-   Document
-   Image
-   Map
-   Object
-   Publication

As shown earlier, the CFT translates:
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

It does this by following rules that tell the CFT to replace `Category 08: Communication Objects, Documentary Objects, Graphic Documents` with `Image` and then append the tail which is `Photograph, Negative`. The next section explains rules.

## Translation Rules

The translation rules are contained in a *translation table* file which is a spreadsheet of rows and columns in CSV format. CSV stands for comma-separated values.

Each row in the translation tables defines one translation rule.

Every rule column is optional except for `Category` and `Translation`.  If the `Category` or `Translation` columns are blank, the CFT ignores the entire row. This allows you to place
blank rows between groups of rules.

The CFT ignores Nomenclature rows having a `level` column value of 1 or 2 because they do no correspond to a leaf term.
A level 1 row only has a category value. A level 2 row has a category and a class.

the CFT processes the Nomenclature terms one at a time to translate them into corresponding Common Facet terms. For each Nomenclature term, the CFT looks for a matching translation rule by starting with the first rule in the translation file, and going to the next rule, until it finds a match.

To find a matching rule, the CFT interprets each rule by comparing the rule's A - F column values, from left to right, against the corresponding values from the Nomenclature row being processed. If *every* non-blank rule column value matches the corresponding Nomenclature row value, the CFT applies the rule, otherwise it skips to the next rule. the CFT only applies one rule to a row.

**Important:** More restrictive rules must occur in the translation file *above* less restrictive rules, otherwise, the CFT will apply a less restrictive rule before it encounters the more restrictive rule. For example, a rule that applies to *any* Nomenclature row having a certain class, must appear *after* a more restrictive rule that applies only to rows of that class that have a specific sub-class or primary value.

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
G | Translation| A pattern specifying the Common Facet term. The pattern contains one or more of the substitution elements explained in the next section. 
H | Replace    | A pair of values in double quotes, separated by a comma, specifying before and after values. the CFT applies the replacement to the translated text after peforming the translation.
J |Notes       | Comments (ignored by the CFT)

### Substitution Elements

The `Translation` column of a translation rule must contain one or more of the following substitution elements:

Substitution  | Meaning
--- | ---
`{class}`     | The value of the `Natural_Order_EN_Class` column of the Nomenclature row. Used when the Nomenclature class should be included as-is in the resulting Common Facet term.
`{sub_class}` | The value of the `Natural_Order_EN_Sub_Class` column of the Nomenclature row. Used when the Nomenclature sub class should be included as-is in the resulting Common Facet term.
`{tail}`      | The tail portion (see explanation above) of the Nomenclature term. Used for most rules.
`{leaf}`      | The leaf term (see explanation above) of the Nomenclature term. Used instead of `{tail}` only when the tail value contains more levels of information than are necessary for the resulting Common Facet term.

The `{tail}` and `{leaf}` elements are mutually exclusive and so only one or the other should be used. These two terms
are only ever used at the end of the translation text.

Examples:
```
Transportation|{sub_class}|{tail}
Object|Tools & Equipment|{class}|{tail}
Object|Armaments|{leaf}
```

## Translation Process

The CFT processes one Nomenclature row at a time. When the CFT finds a matching rule for the row, it applies the rule to the row as follows:

1.  It performs the substitutions listed above.

2.  If the rule's `Replace` column is non-blank, the CFT makes the replacement to the translated text. For example, it changes  
`Structures, Commercial, Lodging Facility, Hotel` to `Structures, Commercial, Lodging, Hotel`.

The resulting string becomes the Common Facet term.

`Object|Built Environment|*` becomes ...

`Object|Clothing|{sub_class}|*` becomes ...

`Object|Writing|{leaf}` becomes ...
