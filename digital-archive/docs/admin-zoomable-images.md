# Zoomable images

The Digital Archive supports zoomable images using [OpenSeadragon](https://openseadragon.github.io/) as the viewer. It expects tile
sources created by the [Zoomify](https://openseadragon.github.io/examples/tilesource-zoomify/) desktop program for Windows.

To make an image zoomable is simply a matter of creating
tiles from the image’s high resolution file and then uploading a folder containing the tiles to the appropriate location on the server. When the Digital Archive software detects the existence of tiles for an item’s image, it automatically displays the image using the OpenSeadragon viewer.

---

!!! note ""
    You must be able to upload files to your Digital Archive webserver to perform these steps.

## Create tiles
1.  Choose the high resolution file to be made zoomable. Use a TIF image if available instead of a JPEG image.

1.  Copy the high resolution image to a temporary location such as a folder on your desktop.
    Do not use a Dropbox folder because doing so will cause Dropbox to start syncing the generated
    tiles to the Dropbox cloud.

1.	Run the `Zoomify Unlimited Converter.exe` program which is located in the `Digital Archive SWHPL\Zoomify` Dropbox folder.

1.  Choose these options:

    -	Set Output Path to `Same as input file`

    -	Set Output Format to `Zoomify folders`

    -	Leave  JPEG Compression Quality setting at `80`

    -	Leave the Compression Format setting at `JPEG Tile Compression`

1.	Drag the high resolution file from the item’s Dropbox folder onto the converter (or choose `Open` from the converter’s menu).

1.	The conversion begins automatically and typically takes only a few seconds.

1.	The generated tiles folder will appear in the folder containing the high resolution image.
    The tiles folder name will be the same as the name of the image.

## Upload tiles to the Server
1.	Rename the newly created tiles folder to the item’s Identifier number.

1.	Transfer the entire output folder to the server. See [upload methods](#upload-methods) below to learn how.

1.	Delete the temporary folder you created earlier since you no longer need any of those files.

1.	Go to the item in the Digital Archive and verify that the image is zoomable.

    !!! Note "Important"
        In order for a zoomable image to display, the item must already have a JPEG image attached to it.
        The JPEG is necessary to allow the user to toggle between the zoomable and web-size images.
        If the item that has no JPEG image, attach one in the usual way.

## Multiple zoomable images 
1.	If the item has more than one image, e.g. a newspaper with eight pages, follow the steps above to
    create one folder of tiles for each image, but give each folder a unique
    name e.g. `1234-001, 1234-002, 1234-003` etc. where `1234` is the item’s identifier.

1.	Create a single folder for the item named using the item’s identifier.

1.	Move the tile folders into this single folder. The structure should be as shown below. 


1.	Upload the single folder with all of its subfolders to the server as described above. The Digital Archive
    software will automatically detect that the item has multiple zoomable images and display them appropriately.

```
    1234  
        1234-001  
        1234-002  
        1234-003
```

## Tag the Item as zoomable
1.	Edit the item and choose the `Tags` tab.

1.	In the `Add Tags` box type `Zoomable`  (it will start to fill in automatically as you type)

1.	Click the `Add Tags` button

1.	Click `Save Changes`

1.	Note that the tag simply makes it easier for people to find the image.
    The image will be zoomable whether you tag it or not.

## Upload methods

**Method 1:**

Use FTP to simply upload the entire folder, subfolders, and files. Note that a very large image will
have hundreds of tiles in multiple folders and can take a minute or more to upload. It also chews up bandwidth
and will slow your internet connection. Though this method is slow, it’s simple and easy if you are just creating a few zoomable images.

- Run FileZilla or other FTP program and connect to the server.
- Navigate  to `public_html/digitalarchive/files`
- Drag the tiles folder to the remote zoom folder. Be sure to drag onto the zoom folder itself, and not onto one of the tiles folders.

**Method 2:**

Zip everything into a single file and upload the zip file to the zoom folder on the server.
This method  involves more steps, but is much  faster because uploading one large file takes a lot less
time than FTPing several folders that each contain dozens of files.

- Zip the zoom tiles folder into a single zip file
- Log into the cPanel for Reclaim Hosting
- Choose the File Manager
- Navigate to `public_html/digitalarchive/files/zoom` 
- Click the `Upload` button in the top menu. A new tab opens with an upload area.
- Drag the zip file from your computer to the upload area
- When the upload reaches 100%, close the tab.
- Click the `Reload` button above the file listing so that you can see the zip file.
- Right-click the zip file, choose `Extract`, and click `Extract Files` on the dialog box
- When the unzip finishes, close the `Extraction Results` window
- Delete the zip file by right-clicking on it and choosing `Delete` or pressing the `Delete` key
- On the Trash dialog, check the `Skip` box and click the `Confirm` button


