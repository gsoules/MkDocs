
# Relationship Rules

The validity of a relationship between any two items is enforced by rules that ensure that each item has the right Type and Subject for the relationship. For example, only people can captain a boat. Therefore, in the captain of relationship, the first item must be a person and the second must be a vessel. When the direction of this relationship is applied in reverse, the first item must be a vessel which is captained by a person.

Though archivists are careful to properly enter data into the Archive, it’s easy to make mistakes and so the Digital Archive software catches and prevents them whenever possible. When an archivist adds a relationship between two items, the software checks the rules for that particular relationship and only allows it if both items satisfy the relationship’s rules and direction. If this validation fails, the software tells the archivist what is wrong and what correction is necessary.

Rules help ensure data integrity by preventing unintended relationships from creeping into the Archive by mistake or due to improper understanding of how two items relate to each other. While use of rules is not required, they make the archivist’s life easier and provide end users with more reliable information.
For Archivists

Chances are that you will never have to add or edit rules because once rules  have been established, they rarely change. However, as you add new items to your Omeka database, you may occasionally encounter a situation where no existing rule matches the circumstances and so a rule needs to be added or modified.
Editing a Relationship Rule

To add, edit, or remove a relationship rule, first go to the Relationships page shown below by clicking on the Relationships button at the bottom of the left menu in the admin interface.

Next, click the green Edit Relationship Rules button to go to the Edit Relationships Rules page shown below. At the bottom of the page (not shown) is a green Add Relationship Rule button that you can click to add a new rule.

Rules appear in alphabetical order to make them easier to find in the list. That’s why the rule numbers are not in numerical order.

To edit or remove an existing rule, click the black arrow that appears at the far right of the rule you want to edit. This expands the row to let you edit the rule or its description. There is no field for the rule number which is chosen by the Digital Archive software. A Remove button appears if the rule is not being used by any Relationship Types. You cannot remove a rule that is in use.

The sections below describe the Description and Rule fields shown above.

Description

The Description is a concise statement that summarizes the rule so that you’ll know what the rule is for when using it to specify a relationship type. The Description also appears in error messages when rule validation fails. When adding or editing a rule’s description, make sure the words you choose are consistent with the descriptions for existing rules.

Rule

In the example above, the rule means that the Omeka item to which the rule applies must have a Type element that starts with “Reference” and a Subject element that starts with either “Businesses”, “Organizations”, or “People”.

Specifying a rule is a bit tricky because you must do so precisely using the proper element names like “Type” and “Subject” as well as the correct syntax for Regular Expressions as explained in the MySQL documentation; however, if you look at a number of rules you’ll notice that they all follow the same pattern and you should be able to edit an existing rule, or create a new rule by, simply following the pattern carefully.
For Developers

This section explains relationship rules in detail. It will be helpful if you will be using the AvantRelationships plugin in your own Omeka project and will be responsible for creating an initial set of relationship rules.

Note that you are not required to specify rules for relationship types. You can use the plugin without rules; however, use of rules is strongly encouraged to enforce relational data integrity.

The screenshot above is repeated here for convenience while reading this section.

The pattern for a rule has the following syntax and semantics:

    A rule consists of a semicolon-separated list of name/pattern pairs. The example above has these two pairs:
        Type:^Reference
        Subject:^(Businesses|Organizations|People)
    Each pair consists of an Omeka Dublin Core element name followed by a colon followed by a pattern (with no spaces in between). In the example above:
        1st pair: The element name is ‘Type’ and the pattern is ‘^Reference’
        2nd pair: The element name is ‘Subject’ and the pattern is ‘^(Businesses|Organizations|People)’
    The pattern is a MySQL Regular Expression (REGEX).
        The ‘^’ means match the beginning of a string.
        The vertical-bar-separated list in parenthesis means match any of the values.
    The name/pattern pairs are ANDed together and the vertical-bar-separated values are ORed together. Thus the rule in the example means that the Omeka item to which the rule applies must have:
        A Type element value that starts with the word “Reference” AND it must have
        A Subject element value that starts with “Businesses” OR “Organizations” OR “People”
    AvantRelationships plugin will translate this example into a SQL WHERE clause like this:
        (_advanced_0.text REGEXP ‘^Reference’ AND _advanced_1.text REGEXP ‘^People’)
    In the WHERE clause above,  ‘_advanced_0.text’ is the value of the item’s Type element text and ‘_advanced_1.text’ is the value of the item’s Subject element text.
    The SQL for a rule gets executed when you add a relationship to an item, or update an existing relationship, to ensure that the relationship is valid for that item and the related item. All of an item’s relationships get validated, and thus rule SQL gets executed, whenever an item gets saved. This is done to protect against the situation where a relationship becomes invalid by virtue of editing one of the item’s elements, e.g. its Type or Subject, in a way that no longer satisfies a relationship’s rules.
