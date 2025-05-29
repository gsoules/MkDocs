## Open a database

-   Use MySQL phpMyAdmin

## Allow remote access to a database

For security reasons, a web host will not allow remote connections to a database
unless you explicitly grant access from the remote source. Follow these steps to
allow phpMyAdmin to remotely access a database.

-   Get the IP address of the computer on which use phpMyAdmin
    -	In a browser window type `myipaddress` in the address bar
    -   Your IP address will appear, or there will be links to sites that will show the address
-	Go to [cPanel](linux-server.md#cpanel)
-	In the `DATABASES` section, click `Remote MySQL`
    -	In the `Add Access Hosts` section, paste the IP address in the **Host** field
    -	Click the `Add Host` button
-   If your IP address ever changes, you'll need to perform these steps again

## Copy a database to use on another server

Follow these steps to copy a production database to use for testing on a local
development server.

### Export SQL database

-   In WHM, open the cPanel for the account
-   In cPanel, choose `phpMyAdmin`
-   Truncate the session table in the left panel
    -   Click `omeka_sessions` table
    -   Click **_Operations_** in the top menu
    -   In the **_Delete data or table_** section (very bottom), click `Empty the table (TRUNCATE)`
    -   Click OK on the confirm dialog
-   Export SQL
    -   Click the database name in the left panel
    -   Click **_Export_** in the top menu
    -   Keep the `Quick` export method and the `SQL` format
    -   Click the **_Go_** button
    -   Save the file on the local computer
    -   Upload the file to the server if it will be imported to a database there

### Create a new database

-   Go to cPanel account for the database e.g. daus
-   In cPanel, open the **_MySQL Databases_** tool
-   Create a new database
-   Add a user to the database
-   Give the database all privileges 

### Import SQL into an existing database using the command line

-   Go to cPanel account for the database e.g. daus
-   Open a Terminal window
-   CD to the folder containing the .sql file
-   `mysql -u root  -p db_name < exported.sql`
-   When prompted, type the root password for the database

To get the root password:

-   Run WHM as root
-   Open a WHM Terminal window (not a cPanel Terminal window)
-   Type `cat /root/.my.cnf`

Example: `mysql -u root -p daus_swhpl < swhpl.sql`

### Import SQL into new local development database

-   Go to phpAdmin on localhost
    -   Run the Laragon Control Panel
    -   Click the **_Database_** button
    -   Click the `phpMyAdmin` link in the top menu
-   Create a new DB with today's date in the name
    -   Click `New` in the left panel
    -   Type a database name
    -   Choose `utf8mb4_unicode_ci` for the character set
    -   Click the **_Create_** button
-   Import the data    
    -   Run phpMyAdmin and import the SQL 
    -   Double click on the name of the new database


### Use the database on localhost

-   Edit `db.ini` to use the new database
    -   Make a copy of the localhost settings
    -   Comment out the original settings
    -   Keep the `host`, `username`, `password`, and `charset` settings for localhost
    -   Change `dbname` to match the new database and make sure `prefix` is set to `omeka_` unless SWHPL in which case it's `omek_`. 
    -   Manually run Omeka on localhost (**DO NOT RUN FROM PhpStorm**)
        -   Go to `http://localhost/omeka/admin/users/login`
        -   Login as a user for the imported database
        -   Go to the **_Appearance_** page and click the **_Navigation_** tab
            -   Change the URL for the `Landing` page to be `http://localhost/omeka/find?query=`
            -   Click the **_Save Changes_** button
            -   Set the Homepage back to the Landing page and save again
-   Get latest files from the server (just ones added/changed since date of last DB)
    -   Go to the `public_html/digitalarchive/files` folder for the site being imported
    -   [Compress the folder into a zip file](/technology/linux-server/#compress-a-large-folder-on-the-server)
    -   Download the zip file into `C:\laragon\www\omeka`
    -   Delete the zip file from the server
    -   Rename `C:\laragon\www\omeka\files` to e.g. `files-swhpl`
    -   Extract or move the `files` folder from the zip file to become the new `files` folder
        (the zip may contain a `files` folder nested in a `files` folder - do the right thing). Extracting a very large zip file can take a long time.
    -   Delete the zip file
-   You should now be able to use the imported site normally on localhost
