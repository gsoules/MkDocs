# Relationship Types

Relationship types make the association of any two items meaningful by indicating the
nature of their relationship to each other. Below are the relationship types for a collection that
has a lot of information about people, organizations, houses, and boats. The choice of
relationship types for a different collection could be different.

![Examples of relationship types](relationship-types-1.jpg)

 This page describes how a Digital Archive site
administrator defines relationship types.

!!! Note "Advanced Topic"
    Adding relationship types is something that an organization does once initially
    and then refines and extends over time. It is not an everyday activity. The instructions
    that follow are intended for an administrator having a solid understanding of
    [The Archive Relational Model](/relationships/archive-relational-model) and good
    computer skills. This information is not intended for archivist who only add and enter items.

---

The type of a relationship must make sense with the two items it relates. For example, only people
can be married to each other. A house can be *designed by* a person or a business, but not by a
place or another house. A place can be the *location of* a house, but a house cannot be located
in an event or in a person. What kind of items are compatible with a specific relationship type
is determined by Relationship Rules.

To get a better sense of relationship types, take a look at the Relationship Types & Rules table.
It lists every type of relationship currently in use among items in the Archive. It also spells
out the rules that apply to the two items involved in the relationship.

An item in a Digital Archive collection can have a relationship with one or more other items.
A relationship's type indicate how two items are related. For instance, a relationship can exist
between two people (Mary is married to John), between a person and a thing (John designed a house),
between a thing and a place (John’s house was located in a village) and so on. To only say that
Mary has a relationship with John, or that John has a relationship with a house, without stating
the nature of the relationship, would not tell the whole story.

## Relationship Direction

A relationship can be either uni-directional or bi-directional. A bi-directional relationship reads the same in both directions. For example, John is married to Mary and Mary is married to John. Married to is a label that describes the relationship in either direction.

A uni-directional relationship reads one way in the forward direction and another way in the reverse direction. For example, John designed a house and the house was designed by John. These phrases sound right because the order of the items matches the direction of the relationship. If the item order or direction is wrong, you end up with the non-nonsensical relationships of a house that designed John, and John being designed by a house. Fortunately, the rules for a relationship’s type ensure correct item order and direction when an archivist adds or edits a relationship.

A uni-directional relationship has two different labels. In the relationship between John and his house, designed is one label and designed by is the other. Each label is the inverse of the other, but they describe the same relationship. If you look  again at the Relationship Types & Rules table, you’ll see that the row for designed has the same Id 17 as the row for designed by. You’ll also see that there is only one row for married to which has Id 8. This is because the married to label is used in both directions. Note that the table lists relationships in alphabetical order by label, which is why the Id numbers do not appear sequentially.

## Genealogical Relationships

An archivist only ever specify a child of or parent of relationship between two people (there is no, grandparent, grandchild, or sibling relationship type) and the software does the rest. This feature sometimes reveals long ancestry chains that would never be apparent when looking at a single item. Two examples in the Archive are item 3687 for Ralph Warren Stanley that shows great great great grandparents, and item 13572 for John Carroll that shows great great grandchildren.

## Relationship Order

All relationships are important, but the curator decides which ones a user will see first when viewing an item. In the Digital Archive, images of an item such as a person, house, or boat, are considered most important and always appear immediately after the item’s metadata. Genealogical relationships come next followed by Reference items that mention the item, and then places where the item is located, and so on. By always presenting related items in the same order, users quickly become comfortable with the interface and know what to expect as they go from item to item.
Viewing Relationships

The fact that every relationship in the archive has a type, direction, and order, makes it possible for the Digital Archive software to present related items most effectively when users are viewing relationships for an item. The software:

    Groups related items by relationship type.
    Groups indirectly related items with their directly related item.
    Displays the relationship label for each group relative to the item being viewed, that is, in a direction from that item to its related items.
    Derives ancestor and descendant chains starting from a People item’s parents and children.
    Lists groups in order of importance.

---


## Editing a relationship type

To get started:

-   Clicking the **_Relationships_** button in the left admin menu
-   On the **_Relationships_** page, click the **_Edit Relationship Types_** button
-   You will see a page similar to the one shown below.

![Examples of relationship types](relationship-types-2.jpg)

At the bottom of the page (not shown) is a green Add Relationship Type button that you can click to add a new type.

Types appear in the relationship order that you want users to see when viewing an item. Drag the rows up or down to change the order and then click the Update Order button at the bottom of the page (not shown) to save it.

To edit or remove an existing type, click the black arrow that appears at the far right of the type you want to edit. This expands the row to let you edit the type. A Remove button appears if the type is not being used as a relationship between two items. You cannot remove a type that is in use. Let’s start with a simple example by expanding the married to relationship type.

The married to type is simple because the relationship direction is bi-directional and therefore both items in the relationship use the same name, label, and rule. The Relationship Rules for this married to relationship require that both items have an Item Type of Reference and a Subject of People.

The only way to make this type even simpler would be to not use rules. You would do that by choosing “Select Below” from the dropdown lists for the Source Rule and Target Rule. However, without rules, an archivist could inadvertently allow a man be married to a boat, or a boat to be married to a house, and so on.

Most relationship types don’t use the Directives and Ancestry fields, but these will be explained later in the Advanced Features section.

Source and Target

The terms source and target refer to the two items that a relationship relates. The distinction is necessary when the relationship direction is uni-directional and therefore the order of the two items matters. The source item is the first item in the forward direction. The target item is the second item in the forward direction. When the inverse of a relationship is used, and thus its direction is reversed, the source item is the second item and the target item is the first item.

The importance of and distinction between source and target should make more sense after discussing the screenshot below which shows the specification of the resided at relationship. Note also that the terms source and target are used only when editing a relationship and at no other time. You only need to fully understand this if you will be responsible for adding or updating relationship types.

The resided at relationship type is uni-directional. The specification above says that the source item must be a person (Reference with subject People) that resided at the target item which must be a dwelling or a place (Reference with subject Dwelling or Places). When the direction of the relationship is reversed, the target item must be a dwelling or a place occupied by a source item which must be a person.

What this means in practice is that an archivist can edit a person item and set a resided at relationship to a dwelling or place item. Alternatively, they can edit a dwelling or place item and set an occupied by relationship to a person item. In the first case, the Digital Archive software will treat the item being edited as the source item. In the second case, it will treat the item being edited as the target item. In either case the software will apply the correct rules to determine if the two items comply with the relationship type.

You choose the Source Rule or Target Rule by picking from a dropdown list as shown below. See the Relationship Rules page to learn how to add or edit rules.

Names and Labels

Continuing with the example for the resided at relationship above, the Source Name and the Target Name are what appear in the Relationship dropdown list when you add a relationship between two items on the Relationships tab. The dropdown list displays the source and target names of every relationship type. The choice for these names is based on what you think will make the most sense to an archivist when they are choosing from the list. End users don’t see these names. What they see are the source and target labels.

The Source Label and Target Label values are what appear to users as the titles of related item groups when viewing relationships. The labels also appear on the arrows in visualization graphs. As you can see for the target item in the resided at example above, the labels can be different from the names.

Notice in the example that the target label  is “Residents,Resident”. By default, the specified label is used for any number of items having this relationship type; however, if English grammar dictates a different label for multiple items than for one item, you can specify the plural spelling followed by a comma and then the singular spelling. Thus in this example, if the Digital Archive software finds more than one resident associated with an item the label for the related item group will be “Residents”; if it finds only one resident the label will be “Resident”.
Advanced Features

Most relationships types are specified using only names, labels, and rules, but to utilize the software’s capabilities for displaying indirect relationships, and genealogies, you need to specify Directives or Ancestry values for certain relationships.

Directives

The Directives value lets you specify which indirect relationships the software will recognize and display to users. The screenshot below shows Directives for the depicts relationship type. The rest of this section uses depicts as an example, but you can specify directives for other relationships.

The comma-separated numbers in the Directives field are Ids of these four relationship types:

    1 is the Id for depicts / depicted by
    -14 is the Id for located at / location of 
    22 is the Id for shows location / on map
    6 is the Id for about / mentioned in

A positive Id indicates the relationship type’s forward direction. A negative Id indicates the relationship type’s reverse direction.

These directives apply when viewing an item that has a depicts relationship to one or more items. In the explanation that follows, each of these items is the “directly related item.” The software applies the directives to each direct relationship as follows:

    Get the item for the target of the direct relationship.
    For each positive Id in the Directives:
        Find every relationship in the database where the relationship type Id is the same as the directive Id and the target of that relationship is the directly related item.
        For each of those relationships, add the source item of the relationship to the list of indirectly related items.
    For each negative Id in the Directives:
        Find every relationship in the database where the relationship type Id is the same as the directive Id and the source of that relationship is the directly related item.
        For each of those relationships, add the target item of the relationship to the list of indirectly related items.
    Display the indirectly related items, grouped by the relationship types represented by the Ids in the Directives.

To better understand the algorithm above, consider item 12316 “Addison Packing Company at Southwest Harbor.” The item, a photograph of a factory, has a depicts relationship to item 13087 which is the Reference item for the factory. That Reference item has direct relationships to several other items. The screenshot below shows just four of the Reference item’s direct relationships which in turn are indirect relationships to the photograph.

The idea behind indirect relationships is to provide context for the item a user is viewing. The purpose of Directives is to specify which indirect relationships the software displays so that the user is not presented with an overwhelming amount of information. If the user wants to know more about the factory than is shown above, he or she can click on the graphic for the factory Reference item to view that item and all of its relationships.

The algorithm for applying the Directives “1, -14, 22, 6” results in the visualization above showing relationship types 1 (“Images”), 14 (“Located At”), 22 (“On Map”), and 6 (“Mentioned in”). The quoted values in parenthesis are the label values for the relationship types. Explained another way, the Directives caused the software to:

    1: Find all other images (in addition to item 12316) that depict the factory.
    -14: Find a Reference item for the location of the factory.
    22: Find a Map showing where the factory was located.
    6: Find a document that tells a story about the factory.

In the relationships for Ids 1, 22, and 6, the factory Reference item in the center of the visualization is the target of the relationship from the related item to the factory Reference item. In the relationship for Id -14, the factory Reference item is the source of the relationship from the factory Reference item to the Apple Lane Reference item. Specification of a negative Id (-14) instead of a positive Id (14) is what tells the software to look for inverse indirect relationships.

Note that the Digital Archive specifies Directives only for the depicts and shows location of relationship types. The depicts relationship is used to relate images and shows location of is used to relate maps. Maps are similar to images in that maps depict places. In practice, these are the cases where indirect relationships make most sense in the Archive, but you may find other useful cases in your collection.

Ancestry

The Ancestry value lets you specify if and how the software displays genealogical relationships. The screenshot below shows the specification of an Ancestry value for the child of relationship. In the Archive, this relationship is used with people but a child relationship could be used with other types of items in a non-genealogical hierarchy.

The Ancestry specification applies when viewing an item that has a child of relationship to one or more items, for example, a mother and/or a father. When adding this relationship, an archivist can choose either child of or parent of depending on which item is being edited (the child or the parent).

The software applies the Ancestry to the source item in a child of relationship by finding the source item’s:

    Siblings
    Ancestors
    Descendants

Siblings are items that have a child of relationship to the same parent items as the item being viewed. For instance, if the user is viewing Louise who is a child of Frank, then every other item in the Archive that is also a child of Frank is a sibling of Louise. The logic treats half brothers and half sisters as siblings. For example, if Louise is Frank’s daughter from his first marriage, but Frank had another child, Carol, with his second wife, then Louise and Carol are siblings by virtue of having the same father.

Ancestors are the items in the chains of child of relationships from the item being viewed to that item’s parents, grandparents, and so on until the chains end. The plural “chains” considers that one person can have two parents, and each parent can have two parents and so on. The software follows these ancestor chains upward until coming to the end of each.

Descendants are the items in the chains of parent of relationships (the inverse of the child of relationship) from the item being viewed to that item’s children, grandchildren, and so on until the chains end. The plural “chains” considers that one person can have multiple children, and each child can have multiple children and so on. The software follows these descendant chains downward until coming to the end of each.

By virtue of specifying an Ancestry value, you tell the software to apply its ancestry logic to the relationship. The syntax of the value is what dictates the actual words the software will use to label the related items groups when displaying siblings, ancestors, and descendants. The syntax rules are explained below. The Ancestry specification in the example above is provided here as larger text for easier reading.

Siblings,Sibling; Parents,Parent:Grandparents,Grandparent:Great *; Children,Child:Grandchildren,Grandchild:Great *

    The Ancestry specification is divided into three semicolon-separated groups for siblings, ancestors, and descendants.
    Within the ancestors and descendants groups are colon-separated levels containing one word pair for each level. The siblings group has just a single word pair.
    The comma-separated word pairs are the plural and singular versions respectively of a word, for example “Grandchildren” is the plural of “Grandchild”.
    Spaces are allowed before and/or after the semicolons and colons.
    You can specify terms for as many ancestor or descendant levels as you like. The example shows just three levels (Parent, Grandparent, and Great *) where the asterisk means to use the last term “Great ” as a prefix for levels four and above. The software automatically applies the prefix to the term used for the previous level. For example, it prefixes level 2’s “Grandparent” with “Great ” to get “Great Grandparent” at level 3, and prefixes level 3 to get “Great Great Grandparent” at level 4 and so on.
    The example uses words commonly seen in English genealogical terminology, but you can specify any words you prefer.

Note that the Digital Archive specifies Ancestry only for the child of relationship.

## Searching for relationships

Administrators can search for items with specific relationships using the Relationship options at the bottom of the Advanced Search page in the admin interface as shown in the screenshot below.

![Searching for relationships](relationship-types-1.jpg)
