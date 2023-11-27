# Linux server administration


This page explains how to perform Digital Archive related web host administration tasks
on an [InMotion](https://inmotionhosting.com/) virtual pritave server (VPS).

---

!!! warning "Caution"
    This documentation on this page assumes that you already know, or will learn, how to perform basic
    system adminstration tasks. For example, you must be able to navigate the file system, edit and delete
    files, and be familiar with system administration duties such as database management, permissions,
    FTP, and such. If these things are foreign to you, **do not** attempt to perform these tasks.

---

## WHM

WMH stands for Web Host Manager. All of the Digital Archive sites are hosted on a dedicated Linux server which you manage using [WHM](https://cpanel.net/products/).

To learn more about WHM, visit <https://docs.cpanel.net/whm/>

!!! note "Tip"
    Use the search box at the top to quickly find a feature. For example, as you type `ftp`,
    the features will immediately narrow down to just those related to FTP. This same technique
    works in cPanel.

---

## Upload and extract a zip file

Follow these steps to upload a zip file to the web server and extract (unzip) its contents.

!!! note
    A zip file's contents are always extracted into a new folder having the same name
    as the zip file. The contents are never extracted directly into an existing folder.
    As such, you may have to move the contents after you unzip them.

### Upload the zip file

-   Go to cPanel and choose `File Manager`
-   Navigate *into* the folder where a new folder should be created for the zip file contents.  
    For example, if uploading an Omeka plugin, navigate into the `plugins` folder.
-   Click `Upload` in the top menu        
-	Select or drag-in the zip file to begin uploading it
-   Wait for the upload to complete. When complete, the progress bar will:
    -   Show 100% *and* change color from blue to green  
        !cPanel(linux-server-2.jpg)
-   Click the `Go Back to` link at the bottom of the page to return to the parent folder
-   Verify that the zip file is there. If not, click `Reload` in the menu above the file list


### Extract the zip file contents

-	Right click on the zip file name and choose `Extract`
-   Click the `Extract File(s)` button
-   On the `Extraction Results` dialog, click the `Close` button
-   A new folder will appear having the same name as the zip file
-   If you don't see the folder, click the `Reload` button

### Delete the zip file
-   Right click on the file name and choose `Delete`
-   On the `Trash` dialog, check the box that says `Skip the trash`
-   Click the `Confirm` button

---

## Tips & Tricks
-   Use <https://skipdns.link> to access a site that's not accessible before switching DNS or namesevers.
-   Use yum instead of pip to install on centos.
-   Use <https://www.whatsmydns.net/> to see what DNS a site is using from various locations

## Compress a large folder on the server using zip

Use the zip command to avoid issues using the cPanel Compress feature. Also, the zip
command reports what it's doing. As an example, to compress the `files` folder of a Digital Archive
installation:

-   Open a terminal window
-   cd to the `digitalarchive` folder
-   Type the command below

```
zip -r file-name.zip directory
```

## Compress and extract a large folder using tar

Compress
```
tar -czvf files-name.tar.gz directory
```
Extract
```
tar -xzvf files-name.tar.gz
```

##### What to do with the download file

Download files are in tar.gz format. Follow these steps to get the contents.

-   Download the file to the local computer
-   Upload the file to a temp directory on the server
-   Extract the contents on the server
-   Use the files on the server or download them to the local computer

---

## Advanced System Administration

### Configure PHP settings

To specify PHP configuration settings for a single site:

-   Log into WHM
-   Choose `List Accounts`
-	Go to cPanel for the `digitalarchive.us` domain
-   Choose `MultiPHP INI Editor`
-   Select the `Basic Mode` tab
-   Choose the site from the dropdown menu
-   Make the desired setting changes
-   Click the `Apply` button

### Contact Manager

To control what notifications get emailed to you as the WHM administrator:

-   Log into WHM
-   Go to `Contact Manager`

Use the `Communication Type` tab to set the level of notification for Email (recommend `High only`).

Use the `Notifications` tab to set the importance of various kinds of notices. Not all notices
are listed. If you are receiving unexpected emails for notifications you don't want to see, contact Inmotion support.


### Disk Usage

To determine how much disk space each site it using:

-   Log into WHM
-   Choose `List Accounts`
-	Go to cPanel for the `digitalarchive.us` domain
-   Choose `Disk Usage`
-   Scroll to the bottom of the page where disk usage is listed by directory
-   Expand the `domains` directory to see usage for each domain 


### View logs for child processes
To see if any sites are hitting their `max_children` limit, open a WHM Terminal window and type the command below:
```
cat /opt/cpanel/ea-php81/root/usr/var/log/php-fpm/error.log |grep max_children
```

To change the `max_children` limit for an individual site:

-   Log into WHM
-   Go to `MultiPHP Manager`
-   Choose the `User Domain Settings` tab to see a list of sites
-   Find the site of interest and click its `PHP-FPM Settings` button
-   Change the value of the `Max Children` field
-   Click the `Update` button at the bottom of the page
-   To go back to the list of sites, click `Go Back To User Domain Settings`


### View the CSF config file

-   Log into WHM
-   Choose `Terminal`
-   Type `cd /etc/csf`
-   Type `less csf.conf`
-   Use the up and down arrow keys to scroll a line at a time
-   Type `q` to quit


### Check the status of SSL certificates

-   Go to the cPanel for `digitalarchive.us`
-   Choose SSL/TLS Status in the Security section


### Check server status and uptime

`WHM > Apache Status`

### Blocked IP addresses
To view blocked IP address, and to perform other IP operations:

-   Log into WHM
-   Go to `ConfigServer Security & Firewall`

To check for a blocked IP address:

-   Scroll to the `csf - ConfigServer Firewall` section
-   Paste the IP address in the text field next to the `Search for IP` button
-   Click the button


### Edit the crontab file

-   Open a WHM Terminal window
-   `export EDITOR=nano`
-   `crontab - e`

### Reboot the server

`WHH > System Reboot > Graceful Server Reboot`

---

