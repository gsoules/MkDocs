# Installing a new Digital Archive site

This page explains how to install and configure a new Digital Archive installation
on a [reclaimhosting.com](super-web-host.md) server. You can also read [Omeka's installation instructions](https://omeka.org/classic/docs/Installation/Installation/); however, this
page covers installation of Omeka Classic and much more.

---

Many steps are required to install the Digital Archive. They are listed on this page in the order
in which you must perform them.

> The navigation panel at left shows all the steps

## Prerequisites
The first step is to:

-   Verify that the web host meets the necessary requirements
-   Choose an installation name
-   Decide where to install the Digital Archive files on the server

**Hosting requirements**

The web host must be an Apache web server that satisfies the 
[system requirements](https://omeka.org/classic/docs/Installation/System_Requirements/)
for [Omeka Classic](https://omeka.org/classic/). AvantLogic uses
[Reclaim Hosting](https://reclaimhosting.com/) as its host.
Learn now to [Create a new Reclaim account](super-web-host.md#create-a-new-account).

**Installation name**

Some of the installation steps require that you specify an installation name. Choose a concise and
meaningful name that you and others will recognize when performing system administration. An acronym
is usually a good choice. For example, the installation name for the Southwest Harbor Public Library is `swhpl`.
Use the name you choose in subsequent steps that refer to the *installation name*.

**Installation folder**

!!! danger "Important"
    **Do not** create the installation folder at this time. It will get created in a subsequent step.

All of the Digital Archive files and folders will be installed within a single folder on the server.
The folder can be:

- The Apache server's `public_html` folder, *or*
- A subdomain's folder

Below are examples of an *installation folder* named `digitalarchive`.
```
public_html/digitalarchive

mysubdomain.avantlogic.net/digitalarchive
```

>   If you want to install in a subdomain,
    [create the subdomain](super-web-host.md#create-a-subdomain) now.

## Create a MySQL database

A new Reclaim Hosting account does not come with a database.  
Follow the steps below to create a new empty database and user for the Digital Archive.

!!! note "Important"
    [cpanel] will automatically prefix any database or user name that you choose with the
    first seven letters of the domain name, followed by `_`. For example, if you specify
    the name `foo` and the domain name is `avantlogic` the actual name will be `avantlog_foo`.
    Keep this in mind because the name you choose will really be a suffix.

    Note that if you install the Digital Archive in more than one subdomain on the
    same host, the corresponding database and user names will all share the same
    prefix. As such, the steps below recommend different choices for subdomains.

### Create a database

-	In [cpanel] go to the `DATABASES` section and click on `MySQL Database Wizard`
-	In wizard Step 1:
    -   Decide on the database name suffix
    -   If the installation folder will be in `public_html`:
        -   A good choice is `omeka`
        -   Example: `avantlog_omeka`
    -   If the installation folder will be in a subdomain:
        -   A good choice is the *installation name*
        -   Example: `avantlog_swhpl`
    -   Enter the database name in the `New Database` field
-	Click `Next Step`

### Create a user

-	In wizard Step 2:
    -   Decide on the user name suffix
    -   If the installation folder will be in `public_html`:
        -   A good choice is `archivist`
        -   Example: `avantlog_archivist`
    -   If the installation folder will be in a subdomain:
        -   A good choice is the *installation name*
        -   Example: `avantlog_swhpl`
    -   Enter the user name in the `Username` field
-   Click the `Password Generator` button
-   In the popup dialog:
    -   If you don't like the password, click the `Generate Password` button to get another
    -   **Copy the password to a password vault or other safe place**
    -   Click the checkbox confirming that you copied the password to a safe place
    -   Click the `Use Password` button
    -   The two password fields get filled in with the generated password automatically
-	Click `Create User`
-	In wizard Step 3, Check the `ALL PRIVILEGES` checkbox at the top
-	Click the `Next Step` button

### Add a MySQL Workbench connection

-   [Add the database to MySQL Workbench](super-mysql-workbench.md#add-a-database-connection)

## Copy a MySQL database

!!! warning ""
    **Skip this step** unless you need to copy an existing database from another Digital Archive
    installation

These instructions use [MySQL Workbench](super-mysql-workbench.md) instead
of [phpMyAdmin](https://www.phpmyadmin.net/).
With a large database, phpMyAdmin is likely to timeout whereas MySQL Workbench will run
until the import completes.

### Export a MySQL database to a `.sql` file

-	From [cpanel], run `phpMyAdmin`
-	On the far left, click on the <name-of DB-to-export> database
-	In the top menu, click on `Export`
-	For **Export method** choose `Quick`
-	For **Format** choose `SQL`
-	Click `Go`
-	When the `Save` dialog appears, choose a location to save on local computer  

### Create an empty database
If you have not done so already, create a database and add it to MySQL Workbench
following the instructions above to [create a MySQL database](#create-a-mysql-database).

### Import a MySQL database from a `.sql` file

-	Run MySQL Workbench
-	Double click on the name of the new database (make sure the name becomes bold)
-	Choose `File` > `Open SQL Script`
-	Select the `.sql` file exported in the subsection above
-	Click `Open`
-	Click the lightning bolt button to execute the script

## Install Omeka Classic files

Follow these steps to upload the Omeka Classic files to the web server.

-	Download the latest Omeka Classic release from <http://omeka.org/classic/download> as a zip file.
    As of 2/6/2020, the latest release was `omeka-2.7.1.zip`
-	From [cpanel] go to the `FILES` section and click on `File Manager`
-   Navigate to the *parent* of the *installation folder*;
    -   If the parent is `public_html` go to `public_html`
    -   If the parent is a subdomain, go to the subdomain folder  
        for example: `mysubdomain.avantlogic.net`
-   Click `Upload` in the top menu        
-	Select or drag-in the zip file to begin uploading it
-   Wait for the upload to be 100% *and* for the progress bar to **turn green**  
    which can take a while for the ~16MB file
-   Click the `Go back` link at the bottom of the page to return to the parent folder
-   Verify that the zip file is there and if not, click `Reload` in the menu above the file list until the zip file appears
-	To extract the zip file, right click on the file name and choose `Extract`
-	Rename the resulting folder from the zip file name to `digitalarchive`  
-   You have now created the *installation folder* containing the Omeka files
-	Delete the zip file


[cPanel]: super-web-host.md#cpanel
