# Copy a MySQL database

This section explains how to use an existing database for a new or existing installation.

---

## Export database

On the web server that hosts the database you want to copy:

-	Go to [cPanel] and choose `phpMyAdmin`
-	On the far left, click on the name of the database to export
-	In the top menu, click on `Export`
-	For **Export method** choose `Quick`
-	For **Format** choose `SQL`
-	Click `Go`
-	On the `Save` dialog, choose where to save the file on your computer  

## Create new database

If you need to create a new database to copy into, follow the instructions for  
[how to create a database](install-digital-archive.md#mysql-database) for a new
Digital Archive installation.

## Import database

-	Run MySQL Workbench
-   Connect to the database you want to copy to
-	Double click on the name of the database (make sure the name becomes bold)
-	Choose `File` > `Open SQL Script` from the top menu
-	Select the `.sql` file exported in the Export section above
-	Click the `Open` button to close the dialog
-   Make any necessary edits to the SQL
-   Be sure no text is selected or else the next step will try to execute the selection.
-	Click the lightning bolt button to execute the script

## Edit db.ini

If you'll be using the new database with an existing Digital Archive installation, you'll need to
edit the `db.ini` file located in the root Omeka folder as appropriate for the database.