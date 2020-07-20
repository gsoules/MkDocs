# Vocabularies

!!! note
    This section is only a draft, but hopefully it provides some useful information.

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

Terms with an underline come from Nomenclature 4.0. You can click the term to learn more about it.

---

The Common Vocabulary Translator (CVT) translates the nearly 15,000 [Nomenclature 4.0](https://www.nomenclature.info/apropos-about.app?lang=en) terms into a simpler Common Vocabulary terms used in the Digital Archive. The hierarchy for a single Nomenclature can be up to six levels deep, though not every term uses all six levels. The levels are:

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

The Common Vocabulary Translator (CVT) translates Nomenclature terms into a simpler Common Vocabulary terms strings based on a set of translation rules that will be explained later. The rules tell the CVT how to translate the hierarchy shown above into the strings shown below.

```
Object, Built Environment, Building Stone, Dimension Stone, Dressed Stone

Transportation, Carriage, Buckboard

Image, Photograph, Negative
```

### Hierarchy Terminology

#### Leaf
The deepest element in any hierarchy is called the *leaf term*. In Nomenclature, every leaf term is unique which makes it possible to determine the full hierarchy from just the leaf term. In the examples above, the leaf terms are `Dressed Stone`, `Buckboard`, and `Negative`.

To ensure that each leaf term is unique, Nomenclature add words to leaf terms to distinguish them from other leaf terms. For example, in addition to the leaf term `Negative`, there are leaf terms for `Glass Plate Negative`, `Roll Film Negative`, and `Sheet Film Negative`.

The CVT preserves Nomenclature leaf terms -- it never translates them -- to ensure that they are the same as and can be
matched with the same terms used in other applications such as PastPerfect.

Nomenclature 4.0 supports leaf terms in both *inverted* and *natural order*. Examples of inverted order are `Negative, Glass Plate`, `Negative, Roll File`, and `Negative, Sheet Film`. The CVT uses the natural order terms when generating Common Vocabulary terms for the Digital Archive.

#### Tail
To convert Nomenclature terms to Common Vocabulary terms, the CVT puts special emphasis on the *tail* of the hierarchy. The tail consists of the Primary, Secondary, and Tertiarty elements if all three exist. If the term has no Tertiary element, the tail consists of the Primary and Secondary elements. If the term has no Secondary element, the tail is just the Primary element. Some higher level terms have no Primary element, but still have a leaf term which is the Sub Class or Class element. In those cases, the tail is the leaf term.

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

- Common Term
- Local Term that replaces a Common Term locally
- Local Term that does not replace a Common Term

Most terms have four levels or less
Only 5% have five levels
None have six levels

