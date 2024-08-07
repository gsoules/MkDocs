# Linux server administration


This page explains how to perform Digital Archive related web host administration tasks
on an [InMotion](https://inmotionhosting.com/) virtual private server (VPS) with [cPanel](https://cpanel.net/).

---

!!! warning "Caution"
    This documentation on this page assumes that you already know, or will learn, how to perform basic
    system administration tasks. For example, you must be able to navigate the file system, edit and delete
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
-   cd to the parent of the `files` folder
-   Type the command below

```
zip -r files.zip files
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

To determine how much disk space each site is using:

-   Log into WHM
-   Choose `List Accounts`
-	Go to cPanel for the `digitalarchive.us` domain
-   Choose `Disk Usage`
-   Scroll to the bottom of the page where disk usage is listed by directory
-   Expand the `domains` directory to see usage for each domain

To see the size of child folders within a parent folder, in ascending order:

-   Log into WHM
-   Open a Terminal window
-   Navigate to the parent folder
-   Type `du -h | sort -h`

Folders for each domain are in `/home/daus/domains/<site>`


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


To block an IP address:

-   Scroll to the `csf - Quick Actions` section
-   Paste the IP address in the text field next to the `Quick Deny Button` button
-   Type `do not delete` in the comment field (see explanation below)
-   Click the quick deny button

To view all blocked IP address:

-   Scroll to the `csf - ConfigServer Firewall` section
-   Click the `Firewall Deny IPs` button to view the `etc/csf/csf.deny` file
-   When done, click the `Return` button at the bottom of the page

Note that each time a new entry is added to the `csf.deny` file, the oldest entry gets deleted.
You can prevent that from happening by adding `do not delete` as the comment for the blocked IP.
This trick is documented in the comments at the top of `csf.deny`.
The default maximum number of entries is 200, but you could increase it by clicking the `Firewall Configuration`
button and changing the value of `DENY_IP_LIMIT`

### High 5 minute load average alert 

This and similar notices from Inmotion occur when a poorly behaved crawler hits a site excessively.
To find the offender, view the `apachestatus.html` file that's attached to the notice. In the Client
column, look for a pattern of repeated IP addresses that are making `GET /find` requests. Follow
the steps in the previous section to block the address.

Another way to see which IPs are hitting domains:

-   Open a WHM Terminal window
-   Type `cd /var/log/apache2/domlogs` and press Enter
-   Use the `ls` command to see the logs
-   Use `cat`, `tail`, or the nano editor to view one of the logs

You can also open cPanel and run the Metrics > Raw Access tool where you can download the current
and archived logs as a `.gz` file.

### Edit the crontab file

-   Open a WHM Terminal window
-   `export EDITOR=nano`
-   `crontab - e`

### Reboot the server

`WHH > System Reboot > Graceful Server Reboot`

---

