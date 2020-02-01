# Using the Instructions field

Some Digital Archive installations have an `Instructions` field that is used to record information
about work that still needs to be performed on a specific item. In contrast, the `Notes` field
is used for miscellaneous information that is not appropriate for any other field.

This page lists syntax for a variety of instructions, and shows [examples](#examples) at the end. By using the
syntax consistently, you make it possible to search for all items that contain a specific instruction.

The purpose of the `Instructions` field is to let you record important actions that you cannot perform
at the moment, but that you want to remember them so that someone can perform them in the future. 

---

Add Document: *description of document*
:   Add a new item of type Document to the collection.

Add Image: *image filename*
:   Add a new item of type Image to the collection.

Add Reference: *title of reference*
:   Add a new item of type Reference to the collection.  
    *Example:* `Add Reference: Merrill Baxter King House`

!!! note "Add instruction"
    The `Add` instruction is often used along with the `Relate` instruction. What sometimes happens is
    that while working on one item you realize that it should be related to another item that is
    not yet in the collection. The `Add` instruction records that realization so it won't be forgotten.

Attach: `filename`
:   Attach a specific image or PDF file to this item.  
    *Example:* `Attach: Lawler – James Whitmore Lawler (1847-1877).pfd`

Combine: `explanation`
:   Combine this item with one or more other items as described in the explanation.
    Usually used when you find another item that is duplicating this item.

Locate: `image filename`
:   Locate the item’s missing image file and attach it to this item.

Metadata: `explanation`
:   Add metadata to this item as specified in the explanation.

Add Publication: `title`  

Instruction	Use
Add Article: [title]
Add Document: [title]
Add Image: [title]
Add Publication: [title]	•	Add a new Omeka item for the specified title. 
•	Implies also adding metadata and attaching the PDF or image files, 
or writing Instructions for the new item.

Add Article: Merrill Baxter King House
Attach: [PDF filename]
Attach: [Image filename]	•	Attach an existing PDF or Image file to this item.
•	Implies also creating the PDF from an existing .doc file.
Attach: Fuller – George Ripley Fuller (1857-1937).doc

Combine: [explanation]	•	Combine this item with one or more other items and provide an explanation.
Combine: with 12878. This item appears to also be Goose Gables.

In Progress: [initials, explanation]	•	Mark an item currently being worked on.
•	Iinclude your initials and an explanation.

Locate: [title]	•	Locate the item’s missing image file and attach to this item.

Metadata: [explanation]	•	Fill in or set metadata fields.
•	Explain what is needed in which fields, and where to find the information, e.g. Access.
Metadata: Fill in history and significance of the USS Constitution
Metadata: Add Credit
Metadata: Set Creator
Other: [explanation]
	•	Add instructions that differ from the others in this list.
•	Explain what is needed as clearly as possible.

Other: Identify people in photo
Other: Get permission

Relate: [item number]
Relate: [title]	•	Create a relationship between this item and the specified item number or title.
•	If it may not be obvious, also specify the kind of relationship.
•	If the item or title does not exist, also include an Add instruction.
Relate: A.L. Somes Store
Relate: 13292, “is spouse of”

Remove: [explanation]	•	Remove this item from Omeka.
•	Explain why the item should be removed.
Remove: This item is general information that is not directly related to the collection.

Replace: [explanation]	•	Replace the attached file, typically an image. 
•	Explain why and which image to use for the replacement.
 Replace: Use scan from negative instead.

Split: [explanation]	•	Split this item into separate items and provide an explanation.

Update: [explanation]	•	Update information, or correct typos or formatting, in an attached file.
Update: Update document and convert to use Biography template. 
Update: Update Hugh C. Leighton Company.doc

Verify: [explanation]	•	Verify or clarify something about this item and provide an explanation.
Verify: Is this photo taken in front of Seth Higgins Clark House?
Verify: Duplicate of 5531?

Write: [title]	•	Write a new document such as a biography or house history. 
•	If known, indicate where the content can be found, e.g. Access DB. 
•	Use only when there is too much content for the Description field.
Write PDF: Southwest Harbor Fire Department

## Examples

Here are a few examples of instructions currently associated with existing Omeka items. Use the links on the Explore page to search for items with specific kinds of instructions.

- Sometimes more than one instruction may be needed. For example, to relate an article for a house to a new article for the owner of a house use an Add instruction for the house article and a Relate instruction:

    - Add Article: Nathan Clark II
    - Relate: Nathan Clark II

- To attach an existing document to an item and relate to this item’s owner:

    - Attach: Beal's Bowling Alley.doc
    - Relate: Beal - Harvard Riley Beal (1897-1967)

- An instruction to add text to the Description metadata field:

    - Metadata: Add description

- To relate an item to several other items and add metadata:

    - Metadata: Add text from SWHPL 12077 in Access
    - Relate: Dudley Luther Mayo
    - Relate: Sara E.K. May
    - Relate: Eliza Robinson

