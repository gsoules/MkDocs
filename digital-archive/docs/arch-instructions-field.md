# Using the Instructions field

The **Instructions** field lets you record a to-do list of work needed for an item.

Typically while working on an item, you discover incorrect or missing information, or you identify
relationships that should be added, but you don't have time right then make those improvements.
In that situation, use the **Instructions** field to record what you learned so that the knowledge
won't be lost.

See the [examples](#examples) at the end of this page to get a better sense of how to write instructions.

---
## List of instructions

Add Reference
:   Add a new item of type Reference to the collection.  
    *Example:* `Add Reference: Merrill Baxter King House`

!!! note
    The `Add Reference` instruction is typically used along with the `Relate` instruction. What often happens is
    that while working on one item you realize that it should be related to another item that is
    not yet in the collection. The `Add Reference` instruction records that realization so it won't be forgotten.

Attach
:   Attach an image or PDF file to this item.  
    *Example:* `Attach: Lawler – James Whitmore Lawler (1847-1877).pdf`

Combine
:   Combine this item with another item that is nearly identical.  
    *Example:* `Combine: with 10551`

Locate
:   Locate an asset that should be attached to this item.  
    *Example:* `Locate: missing image file for this item and attach`

Metadata
:   Add specific metadata that the item needs.  
    *Example:* `Metadata: description`

Other
:   Do something to this item that is not covered by one of the other instructions.  
    *Example:* `Other: Identify women in photograph`  
    *Example:* `Other: Get permission to make this item public`

Relate
:   Create a relationship between this item and another item.
    If the related item is not in the collection, also include an **Add** instruction for that item.  
    *Example:* `Relate: A.L. Somes Store`  
    *Example:* `Relate: 13292, “married to”`

Remove
:   Remove this item from the collection.  
    *Example:* `Remove: Duplicate of 6472`  
    *Example:* `Remove: Not directly related to the collection`

Replace
:   Replace a file that's attached to this item, typically an image.  
    Explain why and which image to use for the replacement.  
    *Example:* `Replace: Use scan from negative instead`  

Split
:   Split this item into separate items.  
    *Example:* `Split: Create a separate item for each group of similar photos`  

Update
:   Update the item's metadata, or the information in an attached PDF.  
    *Example:* `Update: Address in reference sheet should be 26 Charles Street, not 20`  

Verify
:   Verify the correctness of the information about this item.  
    *Example:* `Verify: Date of birth`  
    *Example:* `Verify: Is this photo taken in front of Seth Higgins Clark House?`  

Write
:   Write a new reference sheet such as a biography or house history.  
    *Example:* `Write: history of the chapel`  

## Examples

Here are a few examples on how to use the **Instructions** field.

- Add a new item to the collection and relate this item to it:
``` plaintext
    Add Reference: Nathan Clark II
    Relate: Nathan Clark II, child of
```

- Attach a document to this item and relate this item to another item:
``` plaintext
    Attach: Beal's Bowling Alley.pdf
    Relate: Beal - Harvard Riley Beal (1897-1967)
```

- Add information to this item and relate it to other items:
``` plaintext
    Metadata: Add description from Wikipedia
    Relate: Dudley Luther Mayo
    Relate: Sara E.K. May
    Relate: Eliza Robinson
```

- Improve the item's metadata:
``` plaintext
    Other: Identify the hotel in the background
    Metadata: Set Circa date based on cars in the parking lot
    Verify: Spelling of family name - is it Elliot or Eliot 
```

