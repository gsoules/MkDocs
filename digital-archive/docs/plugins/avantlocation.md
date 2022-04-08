# AvantLocation

The AvantLocation plugin provides a way for an organization, such as a museum, to track the physical location of an object over time as it moves from one location to another. For example, suppose you have a Digital Archive item for a bird carving that is in storage. You then move the object to be on view in the museum, later move it back to storage, then loan it to to another museum, and finally return it to storage. The plugin lets you record the dates and locations for each of these moves so that the object's Digital Archive item displays a history of where the object has been.

The plugin requires that you have defined four Omeka elements to store the following kinds of location information:

- Permanent storage location
- Temporary storage location
- Location status
- Location history
- Public location (optional)

You can use any names you like for the elements. You will tell the AvantLogic plugin the names of the elements using the configuration options described in the next section.

## Configuration options

AvantLocation has several configuration options. A screenshot showing all the options appears at the end of this section. The first five options let your provide the names of the elements that you are using to track locations. The remaining options let you specify values that affect what information this plugin displays.

---

Storage Location Element
:   Use this option to provide the name of the element that is used to record an object's permanent storage location. Typical values for this element would be a facility, room, shelf, bin, or folder. Use of the [Simple Vocab](https://omeka.org/classic/docs/Plugins/SimpleVocab/) plugin is a good way to provide a list of valid storage locations.

Temporary Location Element
:   Use this option to provide the name of the element that is used to record an object's temporary location when it is not in storage. Typical values will describe where the item resides on a temporary basis, for example, a gallery in your own museum, the name of another museum to which you have loaned the item, or the name of a restoration facility. Use of the [Simple Vocab](https://omeka.org/classic/docs/Plugins/SimpleVocab/) plugin is a good way to provide a list of valid temporary locations.

:   Think of the temporary location as any location that is not the permanent storage location. As such, when you move an object back to permanent storage, you should set the temporary location to blank. You can do this in one of two ways:

    - Choose `<none>` from the dropdown list and the plugin will set the element to blank
    - Choose `Select Below` from the dropdown list

Location Status Element
:   Use this option to provide the name of the element that is used to record an object's location status. Typical values for this element would be On View, In Storage, and On Loan. Use of the [Simple Vocab](https://omeka.org/classic/docs/Plugins/SimpleVocab/) plugin is a good way to provide a list of valid status values.

Public Location Element
:   Use this option to provide the name of the read-only element that is used to store a location value this will be visible to the public. Leave the value blank if you don't show a location to the public. The Public Location element is discussed later in the [Public Location](/plugins/avantlocation/#public-location) section

Location History Element
:   Use this option to provide the name of the element that is used to record an object's location history. The element should be a textarea field which is the default field type. This is explained later in the [Location History](/plugins/avantlocation/#location-history) section.

---

Location History Columns
:   Use this option to provide a vertical-bar-separated list of the names of the columns that will appear as titles in the location history table. A typical value would be `Date|Status|Location|Who`.

Public Location Values
:   Use this option to provide a comma-separated list of the location status values that the public is allowed to see. This is explained later in the [Public Location](/plugins/avantlocation/#public-location) section.

Location Move Date
:   Use this option to provide a date such as `2022-04-07` that the plugin will use when it automatically adds a new first row to the Location History element. Leave the value blank to use the current date.

Location Move By
:   Use this option to provide a the name of a person such as `gsmith` that the plugin will be use when it automatically adds a new first row to the Location History element. Leave the value blank to use the user name of the logged in Omeka user.

---
Here is a screenshot showing all of the AvantLocation configuration options.

![AvantLocation configuration page](avantlocation-1.jpg)

---

## How it works

Whenever you change an object's location status and/or temporary location, the AvantLocation plugin does two things:

- Sets the value of the Public Location element
- Adds a new first row to the Location History element

### Public Location

You will probably want to make all of your location tracking elements private so that the public cannot see them. There is one exception which is the Public Location element. This is an optional, read-only element that the AvantLocation plugin sets for you based based on the value of the private Location Status element and the values of the Public Location Values configuration option.

In the screenshot above, the Public Location Values configuration option is set to `On Loan, On View`. Whenever the value of the Location Status element is set to one of those values, the plugin will set the Public Location element to the same value. But when the Location Status element is set to another value, the plugin will set the Public Location element to blank which means it will not appear at all to public users. For example, when the Location Status is set to `In Storage`, the Public Location element will be set to blank because `In Storage` does not match `On Loan` and `On View`.

### Location History

The Location History element uses a textarea field to maintain a history in reverse-chronological order (most recent move appears at the top of the field). The AvantLogic plugin automatically adds a new first row to this field whenever you change an object's location status and/or temporary location. When the temporary location is not blank, the row shows the temporary location. When the temporary location is blank, the row shows the permanent location. This way you can see where the item has been, even when its permanent storage location has changed.

**Editing location tracking fields**

The screenshot below shows how location tracking elements look on the Edit page.

![AvantLocation configuration page](avantlocation-2.jpg)

In this example, Location Status is `In Storage` and the Public Location Values configuration option is set to `On Loan, On View` and so the plugin will set the value of the Location element to blank. Notice in the screenshot above, the Location field (first field) shows gray text that says "Not shown to the public". That's because the field uses the [AvantElements Placeholder](/plugins/avantelements/#placeholder-option) option to show that text on the Edit page when the field has no value.

You can see that the first row of the Location History field reflects the object's location status and location. The remaining rows show where the object has been for the past few years. The individual values in the Location History field rows are separated by a `|` which the AvantLogic plugin interprets as a table column separator.

You can edit the contents of the Location History element if you need to, for example, to correct a date or the identifier of the person responsible for the move. Just be careful to keep the `|` separators in the right places.

**Viewing location tracking fields**

The screenshot below shows how location tracking elements look when a logged-in user is viewing an item. The gray italic elements names are to remind you that those fields are private.

The table's column titles come from the plugin's Location History Columns configuration option.

![AvantLocation configuration page](avantlocation-3.jpg)

Notice how when the object went back into storage on 2022-04-08, it was stored in a new location. The plugin automatically records the current value of the Storage Location element in the history whenever the Temporary Location element's value is blank or `<none>`. Thus, if the storage location changes, the new location is recorded in the history.

**Changing the location for a batch of items**

When you need to change the location information for a batch of items, such as when loaning several objects to another museum, you can use the Location Move Date and Location Move By fields on the AvantLocation configuration page to set a date and a person identifier that will be used as the Date and Who values in the Location History. This way, the date can reflect the actual date of the move (instead of the date on which you edit the items) and the person can be someone other than the Digital Archive administrator who is making the changes.


## Dependencies
The AvantHybrid plugin requires that the [AvantCommon] plugin be installed and activated.

## Installation

To install the AvantLocation plugin, follow these steps:

1. First install and activate the [AvantCommon] plugin.
1. Download the latest release from <https://github.com/gsoules/AvantLocation>
1. Unzip `AvantLocation-master.zip` into your Omeka `plugins` folder
1. Rename the folder to `AvantLocation`
1. Activate the plugin from the Omeka `Plugins` page

## Warning

Use this software at your own risk.

##  License

This plugin is published under [GNU/GPL].

This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation; either version 3 of the License, or (at your option) any later
version.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
FOR A PARTICULAR PURPOSE. See the GNU General Public License for more
details.

You should have received a copy of the GNU General Public License along with
this program; if not, write to the Free Software Foundation, Inc.,
51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

Copyright
---------

-   Created by [gsoules](https://github.com/gsoules) 
-   Copyright George Soules, 2022.
-   See [LICENSE](https://github.com/gsoules/AvantHybrid/blob/master/LICENSE) for more information.

[AvantCommon]: avantcommon.md







 


