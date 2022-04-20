# MapsAlive

The MapsAlive plugin lets you display your Omeka content (metadata and images) on an interactive map that was
created with [MapsAlive](https://www.mapsalive.com). MapsAlive is a web application that lets you create
interactive maps and diagrams that you can  insert into web pages like this one.

**Try it now with the map below.** Click or touch the red dot markers, pan and zoom the map, and select locations from the menu.
The text and pictures you see are being requested in real time by the plugin from the Southwest Harbor Public Library's
[Omeka database](https://myomekasite.net).

<script type="module" id="ma-85015" src="https://tour.mapsalive.com/85015/mapsalive-module.js"></script>
<div class="ma-85015" data-flex-height="300" style="margin-bottom:12px"></div>

#### Maps that use this plugin
Here are interactive maps that use this plugin:

- [Sanborn 1922](https://mapsalive.com/samples/85023)
- [Colby 1887](https://mapsalive.com/samples/85015)
- [Southwest Harbor, Maine 2015](https://mapsalive.com/samples/85022)

## How it works

The MapsAlive plugins lets your Omeka site act as a MapsAlive [Live Data](https://www.mapsalive.com/docs/livedata-intro/) server.
An interactive map makes requests to the server and the server responds with information from your Omeka items.

It works like this:

-   A user selects a hotspot on your interactive map by clicking or touching it.
-   The map makes a [Live Data request](https://www.mapsalive.com/docs/livedata-request-hotspot/#requesting-hotspot-content) to the plugin to get information for that hotspot.
-   The plugin gets the data from your Omeka database.
-   The plugin inserts the data into an HTML [template](/plugins/mapsalive/#templates) that you specify.
-   The plugin sends the HTML back to the map as a Live Data response.
-   The map displays the information about the hotspot the user selected

## Getting started

To help you get started, here are the steps you'll need to perform to create an interactive map that gets its hotspot
information from your Omeka items.

-   In [MapsAlive](https://www.mapsalive.com):
    -   [Create a new MapsAlive tour](https://www.mapsalive.com/docs/start-first-tour/).
    -   Upload a [map image](https://www.mapsalive.com/docs/ref-maps/#map-image) that shows locations of items in your Omeka database.
    -   Add a few [hotspots](https://www.mapsalive.com/docs/ref-hotspots/#hotspots) to the map and place them on locations of interest.
-   On this plugin's [configuration page](/plugins/mapsalive/#configuration-options):
    -   Create a [template](/plugins/mapsalive/#templates) by copy/pasting one of the examples in this documentation.
-   In MapsAlive:
    -   Code a [request function](/plugins/mapsalive/#request-function that will call this plugin).
    -   Make your hotspots be [Live Data hotspots](https://www.mapsalive.com/docs/livedata-request-hotspot/#live-data-hotspot).
    -   [Call your request function](/plugins/mapsalive/#live-data-hotspot) from each hotspot.
    -   View your map in [Tour Preview](https://www.mapsalive.com/docs/start-tour-preview/)
    -   Test that your hotspots display your Omeka item data.

If you need help using [MapsAlive](https://www.mapsalive.com), contact support@mapsalive.com.    

## Configuration options

The MapsAlive plugin has only one configuration field called [Templates](/plugins/mapsalive/#templates). You use the field to define one or more templates that contain HTML or JSON that the plugin will use when it responds to a Live Data request from the map.

Below is a screenshot showing the configuration page. The parts of the template text that are enclosed inside `${...}` and highlighted in yellow are [specifiers](/plugins/mapsalive/#specifiers) indicating where information from Omeka items will be inserted into the template when the maps makes a Live Data request.

![configuration](mapsalive-1.jpg)

## Templates

Templates specify the form and appearance of the information that the plugin returns in response to a Live Data request from a MapsAlive interactive map. The first line of the template specifies its name and other information. The remaining lines are the template's HTML or JSON.

##### Syntax:

``` plaintext
"Template:" <template-name> “,” <item-identifier> “,” <format>
```

Where:

-   `<template-name>` is a name you choose for the template. Each template must have a unique name and only letters, digits, and `_` are allowed. Template names are case-sensitive.
-   `<item-identifier>` is the name of the Omeka element to be used as the unique identifier for the Omeka items that will provide information for the template. Typically it will be the `Identifier` element, but you can use any element, such as `Catalog #`,that *uniquely* identifies items. If more than one item has the same identifier, the plugin will only get information for one of the items.
-   `<format>` is either `HTML` or `JSON` to describe the contents of the template. Typically you will write templates as HTML, but you can write them in JSON if you want to let the map's JavaScript process and format the data. Use of JSON templates is discussed later on.

Below is an example of a template followed by an example of what the resulting Live Data response might look like. If you compare the two, you'll see that the response is the template filled in with information from an Omeka item.

**Template**

``` plaintext
Template: Example1, Identifier, HTML
<div class='wrapper'>
    <div class='title-element'>${element, Title}</div>
    ${file, fullsize, img}
    <div><a href='${item, url}'>View this item</a></div>
</div>
```

**Live Data response**

``` html
<div class='wrapper'>
    <div class='title-element'>Southwest Harbor Motor Co.</div>
    <img href='https://myomekasite.net/files/thumbnails/10247.jpg' width='300' height='246>
    <div><a href='https://myomekasite.net/items/show/6861View this item</a></div>
</div>
```

The screenshot below shows what the HTML might look like when it appears on a map inside a [popup](https://www.mapsalive.com/docs/ref-popups/) that has been [styled using CSS](/plugins/mapsalive/#styling-with-css).

![hotspot](mapsalive-3.jpg)

## Specifiers

A template will contain one or more specifiers that indicate what kind of Omeka item information should be inserted into the template when the map makes a Live Data call.

There are four kinds of specifiers:

-   [Element specifier](/plugins/mapsalive/#element-specifier)
-   [File specifier](/plugins/mapsalive/#file-specifier)
-   [Item specifier](/plugins/mapsalive/#item-specifier)
-   [Data specifier](/plugins/mapsalive/#data-specifier)

The syntax for a specifier is:

``` plaintext
"${" <specifier-kind> [ <arguments> ] "}"
```

The closing curly brace must be on the same line as the opening curly brace.

Specifier arguments are described later for each kind of specifier.

#### Specifier item index

A specifier can include an optional item index argument to indicate which of multiple items the specifier is for. If you don't provide the item index, it defaults to 1 meaning the first or only item.

To better understand what the item index is for, suppose you have two items about a building. The first item has a photo, but no other information. The second has a description of the building plus another photo. You could use the template below to display the description from the second item and the images from both items.

``` plaintext
Template: Example2, Catalog #, HTML
<div>${element, Description, 2}</div>
<div>${file, img, 1}</div>
<div>${file, img, 2}</div>
```

#### Live Data call

When the map makes a Live Data call to the plugin, it passes item identifiers in the `items` argument. It uses a comma `,` as an Id separator. For example, the map would pass `"1001,1002"` to provide the identifiers for items `1001` and `1002`.

---

### Element specifier

The element specifier requests the value of a metadata element for an Omeka item.

##### Syntax:

``` plaintext
“${element”, <element-name> [ “,” <item-index> ] “}”
```

Where:

-   `<element-name>` is the name of an Omeka element.
-   `<item-index>` is an optional parameter explained in the [specifier item index](/plugins/mapsalive/#specifier-item-index) section above.

##### Examples:
``` plaintext
${element, Title}
${element, Description, 2}
```

#### Unpublished items and private elements

The element specifier only returns a value for published items. It returns an empty string for items that have not been published. For a published item, it will return a value for *any* element including ones you have made private or hidden using a plugin like [AvantCommon](/plugins/avantcommon/#private-elements-option) or [HideElements](https://omeka.org/classic/plugins/HideElements/). So be careful not to include an element specifier for an element that you do not want the public to see.

---

### File specifier

The file specifier requests information about a file, usually an image, attached to an Omeka item.

##### Syntax:

``` plaintext
“${file”, <derivative-size>, <property> [ “,” <item-index> ] [ “,” <file-index> ]  “}”
```

Where:

-   `<derivative-size>` is `thumbnail`, `fullsize`, or `original`. Derivative in an Omeka term that refers to the various sizes of images that Omeka derives from the original image uploaded to an item.
-   `<property>` is `img`, `url`, `width`, or `height` (see the [file specifier properties](/plugins/mapsalive/#file-specifier-properties) section below).
-   `<item-index>` is an optional parameter explained in the [specifier item index](/plugins/mapsalive/#specifier-item-index) section above.
-   `<file-index>` is an optional parameter to indicate which of the item's files the request is for. If the parameter is omitted, the default is `1` meaning the first (or only) file attached to the item. In the examples below, the last three lines are using a file index to request images for the first, second, and third files of the first item.

##### Examples:
``` plaintext
${file, fullsize, img}
${file, original, url, 2}
${file, thumbnail, img, 1, 1}
${file, thumbnail, img, 1, 2}
${file, thumbnail, img, 1, 3}
```

#### File specifier properties
There are four file specifier properties, but usually, you will only use the `img` property.

-   `url` is the location of the file on the Omeka site.
-   `width` and `height` are the dimensions of the image in pixels.
-   `img` returns a fully-formed `<img>` tag for the image. It saves you from having to code the tag yourself and it ensures that the tag includes the image dimensions which are very important.

Below is an example use of the `img` property followed by the &lt;img> tag it creates for you.
``` plaintext
${file, thumbnail, img}
```

``` html
<img src='https://myomekasite.net/files/thumbnails/10247.jpg' width='300' height='246'>

```

#### Image width and height

Always provide the **width** and **height** attributes for an **&lt;img>** tag used to display Live Data hotspot content in a MapsAlive
map. If you don't, the popup may initially appear too small and then resize after the browser has downloaded the image and determined its dimensions. Providing the width and height on the &lt;img> tag results in a better experience for people using your interactive map.

Furthermore, unless the image will be displayed at full size, prevent the image from being stretched, by using CSS to set one dimension and allow the browser to compute the other dimension. The CSS below sets the width to 100% of the width of the image's container. It sets the height to auto to let the browser compute that dimension.

``` css
max-width: 100%;
height: auto;
```
For a complete CSS example and more information, see the section on [styling with CSS](/plugins/mapsalive/#styling-with-css).

---

### Item specifier

The item specifier requests the URL or the Omeka Id for an Omeka item. Note that the Omeka Id for an item is not necessarily the same as the value of the item's `Identifier` element.

##### Syntax:

``` plaintext
“${item”,  <property> [ “,” <item-index> ] “}”
```

Where:

-   `<property>` is `url` or `id`. The URL is the one used to display the item on an Omeka site. The Id is the number that Omeka uses to identify the item in the Omeka database.
-   `<item-index>` is an optional parameter explained in the [specifier item index](/plugins/mapsalive/#specifier-item-index) section above.

##### Example:

The example below shows a template that uses both kinds of item specifier properties.

``` plaintext
Template: Example3, Identifier, HTML
<div>${item, id}</div>
<div>${item, url}</div>
```

The HTML below shows what the template would produce for an Omeka item having Id 102.

``` html
<div>102</div>
<div>http://localhost/omeka/items/show/102</div>
```

--- 

### Data specifier

The data specifier gets a data value that was passed from the map and inserts it into the template. It is useful when you want the map to display information that is not available from an Omeka item. For example, you might have Omeka items with photos of a location on the map, but none on the items have a metadata element that says what the location is. The Live Data call for the hotspot at that location on the map could pass the name of the location.

##### Syntax:

``` plaintext
“${data” [ “,” <data-index> ] “}”
```

Where:

-   `<data-index>` is an optional parameter to indicate which data value the request is for. If the parameter is omitted, the default is `1` meaning the first (or only) data value.

##### Example:

``` plaintext
Template: Example4, Identifier, HTML
<div>${data}</div>
<div>${data, 2}</div>
```

#### Live Data call

When the map makes a Live Data call to the plugin, it passes data values in the `data` argument. When passing more than one value, use `~~` (two tilde characters) as a separator. For example, the map could pass `"Franklin Square~~December 1884"` to provide the two data values `Franklin Square` and `December 1884`.  

---

## Repeat section

A template can contain one *repeat section* to emit the same HTML or JSON repeatedly for a list of items passed to the plugin.

To explain the power of a repeat section, let's first describe a scenario that does not use this feature. Suppose
you have four items where the first item has title text identifying a location and the other three items have photos 
of the location. A map could show the text and three images by using the template below and passing four item identifiers.

``` plaintext
Template: Example5, Identifier, HTML
<div >${element Title, 1}</div>
<div>${file, fullsize, img, 2}</div>
<div>${file ,fullsize, img, 3}</div>
<div>${file, fullsize, img, 4}</div>
```

The template above works well if each hotspot on your map has three photos associated with it; however, by using a repeat section,
you can create a template like the one below that does the same thing as the template above, but will work with any number of photos including zero.

``` plaintext
Template: Example6, Identifier, HTML
<div>${element, Title}</div>
[--
<div>${file, fullsize, img}</div>
--]
```
As shown in the example above, the repeat section is delimited by lines containing `[--` and `--]`. The delimiters must be on their own line with no other text before or after them. The repeat section can contain one or more rows.

### Using a repeat section

To use a template that contains a repeat section, the map makes a Live Data call passing two sets of item identifiers as explained in the Live Data call section below. The first set is used for the specifiers that are outside of (above or below) the repeat section, and the second set is used for specifiers within the repeat section.

The one restriction when using a repeat section is that specifiers in the rows *within* the repeat section cannot use a [specifier item index](/plugins/mapsalive/#specifier-item-index). That's because each row in a repeat section gets its data from just one of the items in the second set of items that the map passes as was just explained.

#### Live Data call

When the map makes a Live Data call to the plugin, it passes identifiers for both the non-repeating and repeating items in the `items` argument. It distinguishes the non-repeating item Ids from the repeating Ids by using `;` as a separator. For example, the map could pass `"1001;2001,2002"` to provide the non-repeating identifier `1001` and two repeating identifiers `2001` and `2002`. The resulting HTML when using template Example6 above might look like this:

``` html
<div>Franklin Square</div>
<img href='https://myomekasite.net/files/thumbnails/franklin_sq.jpg' width='300' height='246'>
<img href='https://myomekasite.net/files/thumbnails/98762.jpg' width='300' height='300'>
```

## Using the plugin with a MapsAlive map

This section explains how to make Live Data calls from your interactive map to the MapsAlive plugin. To understand the explanation you'll need to have read the MapsAlive documentation for using its Live Data feature to [request hotspot content](https://www.mapsalive.com/docs/livedata-request-hotspot/) from a server. The server is your Omeka installation with the MapsAlive plugin installed and activated.

Once you have created a [template](/plugins/mapsalive/#templates), there are two things you need to do using MapsAlive:

-   Add a [Request function](https://www.mapsalive.com/docs/livedata-request-hotspot/#request-function) to the MapsAlive tour for your map.
-   Place [Live Data hotspots](https://www.mapsalive.com/docs/livedata-request-hotspot/#live-data-hotspot) on the map.

#### Request function

A typical Live Data request function for getting content from the MapsAlive plugin is shown below. In this example the function is named `getLiveDataFromOmeka` but you can call it anything you like.

``` javascript
function getLiveDataFromOmeka(items) {
   let api = MapsAlive.getApi();
   let url = "https://myomekasite.net/mapsalive";
   api.liveData.requestHotspot("json", 0, url, "items", items, "template", "mytemplate");
}
```

The URL is the root URL of your Omeka site with `/mapsalive` at the end. Adding `/mapsalive` to the URL causes the MapsAlive plugin to be called with the `items` and `template` arguments passed to it.

The `json` value passed to the `requestHotspot` API method is what you must always specify regardless of whether your template is using HTML or JSON format. The next value `0` tells MapsAlive to only requests the data once and cache the response so that it does not call the MapsAlive plugin more than once for the same hotspot.

You can use the function above for your request function by making these edits:

- Change the URL to be for your Omeka site, but leave `/mapsalive` at the end.
- Change `mytemplate` to the name of your template.

#### Live Data hotspot

The value of the request function's `items` argument comes from a [Live Data hotspot](https://www.mapsalive.com/docs/livedata-request-hotspot/#live-data-hotspot). The value will be different for each hotspot because each one requests information from different Omeka items.

Shown below are examples of calls to the `getLiveDataFromOmeka` function for one of the map's Live Data hotspots. You code the call on the MapsAlive **_Advanced Hotspot Options_** screen as explained in the MapsAlive user guide for a [Live Data hotspot](https://www.mapsalive.com/docs/livedata-request-hotspot/#live-data-hotspot). When a user mouses over a hotspot (or clicks or touches a hotspot), the hotspot calls the function passing the item Ids for that hotspot.

``` javascript
getLiveDataFromOmeka("1100")
getLiveDataFromOmeka("1100,1430,1451")
getLiveDataFromOmeka("1100;1430,1451")
```

The first example above passes just one item identifier whereas the second example passes three. The third example would be for a template that has a [repeat section](/plugins/mapsalive/#repeat-section). It passes one non-repeating item identifier and two repeating item identifiers.

## Using JSON templates

All of the examples in this documentation have been for templates that contain HTML. This is the simplest method and is recommended for most people.

Programmers may choose to use JSON templates if they prefer to only obtain data from Omeka items and write their own JavaScript logic to create the HTML that will present the data.

Below is an example of a JSON template followed by an example of the Live Data response.

``` plaintext
Template: Example6, Identifier, JSON
{
   "title":"${element, Title}",
   "image":"${file, thumbnail, url}",
   "width":"${file, thumbnail, width}",
   "height":"${file, thumbnail, height}",
   "link":"${item, url}"
}
```

```
{
   "title":"Southwest Harbor Motor Co.",
   "image":"https://myomekasite.net/files/thumbnails/10247.jpg",
   "width":"300",
   "height":"246",
   "link":"https://myomekasite.net/items/show/6861"
}
```

**Important**: When you use a JSON template, your map must make [Live Data requests for data](https://www.mapsalive.com/docs/livedata-request-data/) *instead of* making [Live Data requests for hotspot content](https://www.mapsalive.com/docs/livedata-request-hotspot/).

#### Developing a JSON template

The MapsAlive plugin does rudimentary validation of JSON code to ensure that it is well-formed, but if there's an error, it won't tell you where the error is. To determine the cause of a JSON error, try using an online tool like <https://jsonformatter.org/> or <https://jsonformatter.curiousconcept.com/>.

A good way to develop a JSON template is to test the template by calling it directly from a browser before using it in a Live Data call from the map. For example, you could test the template above by typing a URL like this into your browser:

```
https://myomekasite.net/mapsalive?template=Example6&items=1100
```

The browser will display JSON like in the example above.
 
 Note that when you use this technique with an HTML template, the result will also be JSON, but in the form shown below. It's the form that MapsAlive expects for a Live Data response that is returnig HTML. To learn more, see the [JSON response](https://www.mapsalive.com/docs/livedata-request-hotspot/#json-response) section in the MapsAlive user guide.

```
{
    "html":"the HTML from the template"
}
```

---

## Styling with CSS

The examples in this documentation have deliberately been kept simple, but in practice you'll usually want to include CSS class names in your HTML templates so that the map's CSS can style the HTML elements.

The HTML below contains class names `wrapper` and `title-element` that make it easy to apply styling.

``` plaintext
Template: Example7, Identifier, HTML
<div class='wrapper'>
    <div class='title-element'>${element, Title}</div>
    ${file, fullsize, img}
    <div><a href='${item, url}'>View this item</a></div>
</div>    
```

The first screenshot below shows what the HTML looks like without styling and the second screenshot shows what it looks like with styling.

![hotspot](mapsalive-2.jpg)

![hotspot](mapsalive-3.jpg)

The CSS for the second screenshot appears below. You put the CSS for a map's hotspots in the map's CSS section on the [Custom HTML](https://www.mapsalive.com/docs/start-custom-html/?h=custom+htm#css) screen in MapsAlive.

``` css
.wrapper img {
   max-width:100%;
   height: auto;
   border: 2px solid black;
}

.wrapper {
   padding: 4px 12px 0 12px;
   text-align: center;
}

.title-element {
   font-size: 18px;
   font-weight: bold;
   margin-bottom: 4px;
   color: firebrick;
}

.view-link a {
   color: green;
   font-size: 16px;
   text-decoration: none;
}
```




