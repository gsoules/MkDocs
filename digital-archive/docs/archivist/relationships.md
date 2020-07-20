# Relationships


Relationships are the heart and soul of the Digital Archive. They are what make the Archive different from other databases or Omeka projects you may have worked with. Relationships are like the lines that connect the dots in those puzzles you did as a kid. Until you drew the lines, all you saw was dots and numbers, but once you connected the dots, you saw a picture!

Relationships in the Archive are like relationships in the real world. They tell us how two or more people, places, or things are connected to each other. For example, a man owned a boat, resided in a house, and was married to a woman. The words owned, resided in, and married to name the relationships that tell us how the man was connected to the boat and the house and the woman.
Relationship Types

An item in the Archive can have a relationship with one or more other items. Relationship Types indicate how two items are related. For instance, a relationship can exist between two people (Mary is married to John), between a person and a thing (John designed a house), between a thing and a place (John’s house was located in a village) and so on. To only say that Mary has a relationship with John, or that John has a relationship with a house, without stating the nature of the relationship, would not tell the whole story.

The type of a relationship must make sense with the two items it relates. For example, only people can be married to each other. A house can be designed by a person or a business, but not by a place or another house. A place can be the location of a house, but a house cannot be located in an event or in a person. What kind of items are compatible with a specific relationship type is determined by Relationship Rules.

To get a better sense of relationship types, take a look at the Relationship Types & Rules table. It lists every type of relationship currently in use among items in the Archive. It also spells out the rules that apply to the two items involved in the relationship.
Relationship Direction

A relationship can be either uni-directional or bi-directional. A bi-directional relationship reads the same in both directions. For example, John is married to Mary and Mary is married to John. Married to is a label that describes the relationship in either direction.

A uni-directional relationship reads one way in the forward direction and another way in the reverse direction. For example, John designed a house and the house was designed by John. These phrases sound right because the order of the items matches the direction of the relationship. If the item order or direction is wrong, you end up with the non-nonsensical relationships of a house that designed John, and John being designed by a house. Fortunately, the rules for a relationship’s type ensure correct item order and direction when an archivist adds or edits a relationship.

A uni-directional relationship has two different labels. In the relationship between John and his house, designed is one label and designed by is the other. Each label is the inverse of the other, but they describe the same relationship. If you look  again at the Relationship Types & Rules table, you’ll see that the row for designed has the same Id 17 as the row for designed by. You’ll also see that there is only one row for married to which has Id 8. This is because the married to label is used in both directions. Note that the table lists relationships in alphabetical order by label, which is why the Id numbers do not appear sequentially.
Indirect Relationships

When one item is related to another, it is inevitable that the other item is related to yet another item and so on. The idea of six degrees of separation makes for interesting reading on this topic and illustrates how seeing too many relationships can get confusing. In the Digital Archive, when viewing an item, a user sees at most two degrees of separation to related items. The first degree is the relationship from the item being viewed to a directly related item. The second degree is the relationship from a directly related item to an indirectly related item.

The visualization graph below illustrates the indirect relationships a user sees when viewing item 10725, a photograph of a sailboat. The image shows the yawl “Venturer” coming out of a building at the Henry R. Hinckley Company where the vessel was built. The photo depicts the boat and it depicts the company. The graph shows two direct relationships from item 10725 to Reference items for the company and the boat. Each Reference item is directly related to other items shown at the far right. There are more images of the company and a map showing where the company is located. There are also more images of the boat, and a newspaper clipping announcing its launch. Those images, the map, and the clipping are indirectly related to item 10725, the photo of Venturer.

The The Henry R. Hinckley Company Reference item is directly related to other items besides the images and map shown above. All of its direct relationships are shown in the screenshot below. Imagine how cluttered the visualization above would be if it showed all of these direct relationships as indirect relationships. Archivists can configure the Digital Archive software to control which indirect relationships are displayed and thereby prevent information overload for the user.

Note that archivists at the Southwest Harbor Public Library configured the Digital Archive to only show indirect relationships when the item being viewed is of type Image or Map. In practice this works well and provides the right amount of context for the item being viewed.
Genealogical Relationships

While the Digital Archive was not designed as a genealogy tool, it automatically determines ancestor and descendant chains starting from the item being viewed. This ancestry feature works for items of type Reference having a subject of People. It automatically follows child of relationships to locate parents, grandparents, and so on until the chain ends. It follows the inverse relationship parent of to locate children, grandchildren, and so on. The mechanism also automatically identifies siblings

Note that archivists only ever specify a child of or parent of relationship between two people (there is no, grandparent, grandchild, or sibling relationship type) and the software does the rest. This feature sometimes reveals long ancestry chains that would never be apparent when looking at a single item. Two examples in the Archive are item 3687 for Ralph Warren Stanley that shows great great great grandparents, and item 13572 for John Carroll that shows great great grandchildren.
Relationship Order

All relationships are important, but the curator decides which ones a user will see first when viewing an item. In the Digital Archive, images of an item such as a person, house, or boat, are considered most important and always appear immediately after the item’s metadata. Genealogical relationships come next followed by Reference items that mention the item, and then places where the item is located, and so on. By always presenting related items in the same order, users quickly become comfortable with the interface and know what to expect as they go from item to item.
Viewing Relationships

The fact that every relationship in the archive has a type, direction, and order, makes it possible for the Digital Archive software to present related items most effectively when users are viewing relationships for an item. The software:

    Groups related items by relationship type.
    Groups indirectly related items with their directly related item.
    Displays the relationship label for each group relative to the item being viewed, that is, in a direction from that item to its related items.
    Derives ancestor and descendant chains starting from a People item’s parents and children.
    Lists groups in order of importance.

For Archivists

Many of the Relationships pages have a section titled “For Archivists” which contains information intended specifically for Digital Archive users who have a login with administrator privileges. While the general public cannot access “admin” features, this information may be of interest if you would like to know how archivists at the Southwest Harbor Public Library work with the Digital Archive.
For Developers

A few of the Relationship pages have a section titled “For Developers” which contains information to help software developers who are using the free AvantRelationships plugin for Omeka on their own project. While this information is technical in nature, it may still be of interest.