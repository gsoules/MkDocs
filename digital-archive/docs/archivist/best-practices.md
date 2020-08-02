# Best Practices

TITLE

An item can have multiple titles, but only if you can say “Also known as” for the alternate title(s).
People are listed by last name first followed by a hyphen. If the person is living, omit the dates. 
The convention for men is as follows:
LastName - FirstName MiddleNameOrInitial LastName (birthdate-deathdate)
Rich - Clifton Melbourne Rich (1882-1971)
Rich - Merton E. Rich (1927-2010)
Rich - Jasper E. Rich
For women use the maiden name for the initial LastName and also include it in parentheses before their married last name:
	Rich - Meredith Adelle (Rich) Hutchins (1939-2016)
Nicknames for people are included in the Title field as follows:
Bracy - Thelma Gwendolyn (Bracy) Hinckley (1913-2005) aka Gwen

D.	Map Titles
Base map titles start with the date of the map (if known) followed by a brief descriptive title taken from the actual title of the map. Additional descriptive information from the actual map title or other text on the map is included in the Description field.

		1887 Map of Mount Desert Island
		1886 Bird’s Eye View of Bar Harbor, Maine
		1903 Part of Ward 9, City of Cambridge
		1921 Sanborn Map of Manset Shore and Southwest Harbor

F.	Date
Unknown birth or death dates – when you know a person is not living, but we don’t know the birth or death date use a “?”:
Gott - Everett Livingston Gott (1875-?)
Gott - Everett Livingston Gott (?-1954)

H.	Creator
The Creator is the “entity primarily responsible for making the content of the resource”. For Article, Document this is the person who wrote the document (e.g. Riebel - Charlotte (Riebel) Morrill). For a photograph, the creator is the person who took the photograph. It is not necessary to specify a creator for Article, Text items with short general descriptions. The Creator field is optional, but when specified, must match exactly the Title of the item for that creator.

-	Work with the public interface all of the time except when not possible
-	Define vocabuaries for the site
-	Mangage archival copies of files
-	Only upload web-sized images
-	Define an archival file management scheme
-	Scanning (include scanning resolution tree and other files)

---

## Vocabulary term

Use unique leaf terms within the same vocabulary.

Don't use comma in Place names unless for hierarchy e.g. `Bangor ME` not `Bangor, ME`

When mapping to a common vocabulary term, you should usually repeat the common vocabulary term
e.g. `Image, Photograph, My custom term` but not always e.g. if you want to elevate your term
e.g. `Carving`.

## Reference Items
A Reference Item should have no image attached to it because its metadata should either
be all text, or some text plus a PDF file attachment. The Digital Archive does not
enforce this, but it is a best practive. See Cover Images
    A Reference Item *should not have an image attached to it*, but it can have a PDF
    attachment.  
    The Digital Archive does not enforce this guideline, but it is a best practice
    because attaching an image to a Reference Item is inconsistent with the 
    [Archive Relational Model](/relationships/archive-relational-model/) which uses the
    *depicts* relationship to associate a Reference Item with all of its images.
	Just because you have only one image now doesn't mean you won't get more later.
---

Metadata appears in fields with names like Title, Description, and Location. Not every item has every metadata field, only the ones that are relevant and for which we have information. Every item has these metadata fields:

    Identifier – Four or five digit number that is unique to that item.
    Title – Brief description of the item. Some items have more than one title. This is common for boats where the name changed over time.
    Type – The kind of real-world object the item represents. Learn about Item Types.
    Subject – What the item is about. Some items have more than one subject. Learn about Subjects.
