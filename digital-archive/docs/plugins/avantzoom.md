# AvantZoom

The AvantZoom plugin provides image zooming capability using [OpenSeadragon](https://openseadragon.github.io/).

See the documentation for [zoomable images](../administrator/zoomable-images.md) to learn how to make an image zoomable.

---

## Configuration options

AvantZoom has no configuration options.

See also the documentation for [installing AvantZoom](../../../developer/install-digital-archive/#avantzoom).


## Dependencies
AvantZoom depends on the following open source library which is included in the `views/shared/javascripts` folder.
Click the link below to see its copyright and license.

* [OpenSeadragon](https://openseadragon.github.io/) - An open-source, web-based viewer for high-resolution zoomable
 images, implemented in pure JavaScript, for desktop and mobile. 

## Installation

1.  Download the latest release from <https://github.com/gsoules/AvantZoom>
1.  Unzip `AvantZoom-master.zip` into your Omeka `plugins` folder
1.  Rename the folder to `AvantZoom`
1.  Activate the plugin from the Omeka `Plugins` page
1.  In the Omeka `files` folder, create a `zoom/images` folder 
1.  Copy the `images` folder from the `plugins/AvantZoom` folder to the `files/zoom/images` folder
    The `images` folder contains icon used by the OpenSeadragon viewer for the zoom in, zoom out, and other controls
    AvantZoom does not use the folder
1. If not using AvantTheme, edit your theme's `show.php` file as explained below

### Edit show.php

!!! note ""
    Skip these steps if you are using AvantTheme which has built in support for AvantZoom.

The AvantZoom plugin provides everything you need to start using OpenSeadragon, but you must edit your theme's
`items/show.php` file to insert code at both the top and the bottom of the file. The code adds the OpenSeadragon viewer to the Item
page and also makes calls to the AvantZoom logic that configures OpenSeadragon to display an item's image.

The instructions that follow are using the `show.php` from the [Seasons](https://omeka.org/classic/themes/seasons/) theme.
You might need to make different edits for other themes.

First edit the code at the top of `show.php` by replacing the first four lines in the file (shown below) ...

```
<?php echo head(array('title' => metadata('item', array('Dublin Core', 'Title')),'bodyclass' => 'items show')); ?>
<h1><?php echo metadata('item', array('Dublin Core', 'Title')); ?></h1>
<div id="primary">
    <?php if ((get_theme_option('Item FileGallery') == 0) && metadata('item', 'has files')): ?>
```
... with the lines that follow. Note the insertion of `!$zoom &&` in the last line. This condition determines
whether or not to display the OpenSeadragon viewer. When `$zoom` is false, the item's image is not zoomable in which
case, the orgiginal HTML is rendered to display the image in the usual (non-zoomable) manner.
```
<?php
$zoomScript = ImageZoom::generateOpenSeadragonViewer($item);
$zoom = !empty($zoomScript);
if ($zoom)
    queue_js_file('openseadragon.min');
echo head(array('title' => metadata('item', array('Dublin Core', 'Title')),'bodyclass' => 'items show'));
echo '<h1>' . metadata('item', array('Dublin Core', 'Title')) . '</h1>';
if ($zoom)
    echo '<div id="openseadragon"></div>';
?>
<div id="primary">
    <?php if (!$zoom && (get_theme_option('Item FileGallery') == 0) && metadata('item', 'has files')): ?>
```
At the end of `show.php`, insert code just above the call to `foot()` so that the end of the file looks like this:
 
```
<?php
if ($zoom)
    echo $this->partial('avantzoom-script.php', array('viewerScript' => $zoomScript));
?>
<?php echo foot(); ?>
```


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
-   Copyright George Soules, 2017-2020
-   See [LICENSE](https://github.com/gsoules/AvantZoom/blob/master/LICENSE) for more information

