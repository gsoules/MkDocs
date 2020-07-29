# Cover Images for Reference Items

The Cover Image feature allows you to use the image for one item as the representative image for a Reference item, but without attaching the image to the Reference item. A Reference item has no image attached to it because its content is text. When a Reference item does have an attachment, the attached file is usually a PDF document. The cover image appears in the upper left corner of the Reference item’s page as shown in the screen shot below.

Cover Images address the fact that a Reference item generally provides lifelong information about something, like biographical information for a person, or the history of a house, whereas a photograph literally captures a moment in time. Over its lifetime, a person or building may have been photographed many times. Each photograph belongs to its own Image item having metadata describing what’s known about the image, such as when it was taken, where, and by whom.

Despite the need to separate references from images, it’s desirable to associate an image with a Reference item so that when you view the Reference item, a picture of what it represents is prominently displayed. This is where Cover Images come in. In the screenshot below, the portrait in the upper left is the Cover Image for Reference item 13579, but the image itself is attached to item 11562.

For Archivists

The Archive Relational Model allows the lifelong information in a Reference item to coexist with the fleeting instance of a photograph by allowing each Image item to have a depicts relationships to a Reference item, and conversely, allowing each Reference item to be depicted by one or more Image items. The screenshot above shows Reference item 13579 for a women named Annie Downs Clark for whom the Archive contains several images, but only a small amount of biographical information. The portrait of Annie as a young girl that appears in the upper left, comes from Image item 11562 and serves as the Cover Image for item 13579. The metadata for 11562, tells us that the portrait was taken by John C. Ralph around 1899 which would make Annie about 11 years old the day she posed for this picture.

Setting a Cover Image

You set the Cover Image for an item by editing the item and choosing the Cover Image tab which appears when the AvantRelationships plugin is installed. To specify or change the item’s Cover Image, enter the Identifier number of the item containing the desired image, and then click the Save Changes button.

    