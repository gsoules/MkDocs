# Common Vocabulary

The Common Vocabulary is a set of vocabulary terms that multiple Digital Archive sites can
all use in common when choosing values for these metadata fields:

-   **_Type_**
-   **_Subject_**
-   **_Place_**

The purpose of the Common Vocabulary is to ensure cataloging consistency across a 
group of organizations that are sharing their collections with each other using the Digital Archive.
In addition to using Common Vocabulary terms, each organization can use site-specific
vocabulary terms that are tailored to their collection.
Archivists work with both Common Vocabulary and site-specific terms using the
[Vocabulary Editor](/archivist/vocabulary-editor/).

## Terminology

To understand the Common Vocabulary, you must become familiar with the terminology below.

Term
:   A **term** is a *combination of words* that concisely describe or classify something. For example,
    the comma-separated list of words below form a *single* term that describe a photograph
    that was printed using the cyanotype printing process that produces a cyan-blue print.

        Image, Photograph, Photographic Print, Cyanotype

Vocabulary
:   A **vocabulary** is a controlled list of terms that archivists use when cataloging items
    in their collection. Controlled means that archivists choose terms from lists rather then
    typing into a blank field. Choosing from a list ensures consistency and prevents
    archivists from using terms that are not appropriate for the collection.

Hierarchy
:   Individual terms belong to tiered groups of related terms that are each unique, but have something in common.
    The examples below illustrate the meaning of **hierarchy**.

    These two terms are in the `Image` hierarchy:

        Image, Art, Drawing
        Image, Photograph, Photographic Print, Cyanotype

    These two terms are in the `Image, Photograph` hierarchy

        Image, Photograph, Negative
        Image, Photograph, Photographic Print, Cyanotype

    These two terms in the `Image, Photograph, Photographic Print` hierarchy

        Image, Photograph, Photographic Print, Albumen Print
        Image, Photograph, Photographic Print, Cyanotype

Leaf
:   The word or words following the last comma in a term are known as the **leaf**.
    If you think of a hierarchy as a tree with multiple branches, the leaf words are
    the leaves of the tree. Put another way, they are the deepest words in a
    hierarchy. In the examples above the leaf words are `Drawing`, `Cyanotype`,
    `Negative` and `Albumen Print`.

    In the [Common Vocabulary](/archivist/common-vocabulary), and also in
    [Nomenclature 4.0](/archivist/common-vocabulary/#nomenclature-40),
    every leaf is unique. This means that once leaf words are user for one term, those exact words can
    never be used as the leaf for another term. This explains why a term's leaf sometimes
    contains what seems like redundant words. For example, the terms below 
    describe physical structures.

        Structures, Factory, Cannery
        Structures, Civic, Performing Arts, Theater
        Structures, Quarry

    The terms below describe the businesses associated with those structures.

        Businesses, Cannery Business
        Businesses, Theater Business
        Businesses, Quarry Operation                 

    Even though the first three terms are in different hierarchy (`Structures`) than the second
    three terms (`Businesses`), all six terms are in the same **_Subject_** vocabulary and therefore
    must have unique leaf words. To accomplish this, the second set appends `Business` or `Operation`
    to the leaf words in the first set.

Common Vocabulary
:   The **Common Vocabulary** is a set of terms that multiple organizations all use in common
    as a way a providing consistency in these metadata fields: **_Type_**, **_Subject_**, **_Place_**.
    The Common Vocabulary is very large. It contains approximately 15,000 terms.

Site Vocabulary
:   A **site vocabulary** is a set of terms that are specific to one organization's Digital Archive
    site. It only extends, or fills gaps in, the Common Vocabulary and is therefore very small.
    
    A typical site vocabulary, used in conjunction with the Common Vocabulary, might have only a
    few dozen terms or less. An exception would be an organization that wanted to use an entirely
    different vocabulary, such as
    [Library of Congress Subject Headings](http://id.loc.gov/authorities/subjects.html) or
    [AAT](http://www.getty.edu/vow/AATHierarchy?find=booklet&logic=AND&note=&english=N&prev_page=1&subjectid=300311670).
    In that case, they would have a large site vocabulary, but they could still maintain consistency
    with other sites by using **mapped site terms** as will be explained below.

Common Term
:   A **common term** is one that comes from the Common Vocabulary. Most organizations can utilize common terms
    for most of the items in their collection. In cases where there is no applicable common term, an
    archivist can create a **site term**.

Site Term
:   A **site term** is one that does *not* come from the Common Vocabulary. It is specific to an organization
    and is found in that organization's site vocabulary. While a site term is not in
    the Common Vocabulary, more than one organization might be using the same site term. If it becomes known
    that many organizations are using the same site term, that term would become a candidate for inclusion in
    the Common Vocabulary.

    In the [Vocabulary Editor](/archivist/vocabulary-editor/), site terms appear together with Common Terms,
    but they are distinguished from common terms by their font and color. 

Mapped Site Term
:   A **mapped site term** is a site term that is associated with (mapped to) a Common Vocabulary term. By mapping
    a site term to a Common Term, an organization gets the best of both worlds: a site-specific term for their
    organization and a common term that is consistent with terms that all organizations are using.

Unmapped Site Term
:   An **unmapped site term** is a site term that is not associated with (not mapped to) a Common Vocabulary term.
    In practice, an organization will only use unmapped site terms for a short period of time while they are
    deciding which Common Vocabulary terms to map them to. As a general rule, an organization should not use
    unmapped site terms. Even the most unusual item in a collection can be mapped to a Common Vocabulary term
    such as `Object, Other Object` or `Document, Other Documents` or `Image, Other Image` and several other
    catch-all terms.


## Origin of the common terms



## Nomenclature 4.0

The Common Vocabulary terms are generated from Nomenclature 4.0 terms using the
[Common Vocabulary Translator](http://127.0.0.1:8000/developer/common-vocabulary-translator/) software.


