# Archive Relational Model

The Archive Relational Model was developed in 2016 by George Soules of AvantLogic Corporation
in partnership with Charlotte Morrill who had the original vision.
It is a new approach for recording and presenting images and information about people, places,
events, organizations, and objects in the real world. It provides archivists with a structured,
but easy to use method for presenting their collections online in a way that engages users by
making it fun and easy to learn about local history.

AvantLogic developed the model for the Southwest Harbor Public Library in Maine following a lengthy
search for software that would showcase the Library’s large collection of historic photographs,
documents, maps, and research material. The search turned up solutions that display this kind
of information, but none that reveal the real-world interconnections among people, places, and
objects that make our lives rich today and make history so fascinating. Unable to find an existing
solution, AvantLogic opted to use Omeka to create the Digital Archive software and share it with
others as open source.

## Key Concepts

The basis of the Archive Relational Model is that each item in the Digital Archive serves as a
stand-in for something in the real world such as a man or a boat. The key to understanding the
model is to think of the item for the man as the man himself, and to think of the item for
the boat as the boat itself.

Now consider another kind of item in the collection, a photograph of the man on his boat.
Obviously the photograph itself is not the man and it is not the boat. It’s a piece of paper
with chemicals that formed an image showing the man and boat during a moment in time.

Now let’s reinforce the concept of an item being a stand-in. Clearly, a database cannot store
the flesh and blood of a man, the wood of a boat, or a photograph’s paper and chemicals.
It can however store information (metadata) about the man’s life, the boat’s history,
a digital scan of the photograph, and information about the photo such as when and where
it was taken and by whom. This information tells us what the item is a stand-in for and
provides a place to record how one item is related to another.

In the real world, the man owned the boat, and the photograph depicts the man and the boat.
The words *owned* and *depicts* are relationships. The Archive Relational Model lets us record
these very same relationships between the items in the database that stand-in for their real
world counterparts.

Note that the phrasing of a relationship depends on your perspective. The man owned the boat,
but from the perspective of the boat, it was owned by the man. The *owned by* relationship is
simply the inverse of the *owned* relationship. The model and the software allow archivists
to establish relationships between two items from the perspective of whichever item they happen
to be working with.

Most relationships are established between what are called **Reference Items** in the model.
An explanation of this key concept is deferred until later following further discussion of relationships.

## The Importance of a Relational Model

Relationships are what make the world go round. A man and a boat by themselves are not very
interesting until you learn that the man who owned the boat also tended a lighthouse located
on an island where the man and the woman he was married to were the parents of eight children
who were students at a one room school house that has since been restored by the historical society!

An online collection that does not reveal the relationships among its items, serves only as a
repository of information that users must search to locate items of interest. It’s like fingering
through a library card catalog to locate a single book. In contrast, using the Digital Archive is
like seeing a book on the shelf along with the related books that surround it. By looking at the
shelf, you discover other books that you didn’t even know about. The Archive Relational Model
enables this discovery process in the Digital Archive.

The discovery process is fun, but more importantly, it is an essential feature that an
organization must provide if it wants the public to fully appreciate the content of the collection.
However, to provide users with this benefit, archivists must establish relationships between items
in the collection. Fortunately, it’s easy to do and can be performed little by little over time as
resources allow. Users benefit immediately each time a new relationship is added.

## Establishing Relationships

The Archive Relational Model both encourages and enforces good practices for entering item metadata
and establishing relationships between items. The user interface for adding relationships is quick
and easy to use and it prevents an archivist from inadvertently setting inappropriate or non-nonsensical
relationships such as a man married to a boat. This enforcement of referential integrity is possible
because of relationship types and relationship rules.

When an organization first adopts the Archive Relational Model, it defines the kinds of relationships
that make sense for items in the collection. The organization also specifies rules that must be followed
when an archivist adds a specific relationship between two items. An example of a rule is that only a
person can be married to a person. Another rule is that a photograph can only depict an item that is a
stand-in for a person, place or thing. For example, a photograph cannot be married to a person, because
as discussed earlier, the photograph is not the person, but only an image of the person at one moment in time.

In the Digital Archive, an item that serves as the stand-in for a person (or boat, house, business etc.)
is called a **Reference Item**. The concept of a reference is central to the Archive Relational Model.
The next section describes the meaning and use of Reference Items and explains why they are so important.

## Reference Items

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