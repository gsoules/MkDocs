# Digital Archive site maintenance

---

## Plugin and Theme updates

To update the `plugins` and `themes` folders on all Digital Archive sites:

-   Open a terminal window for `digitalarchive.us` using *one* of these methods:
    -   Go to cPanel for `digitalarchive.us` and choose `Terminal`
    -   Use PUTTY
-   `cd bin`

-   Choose one of these commands:
```
$ sudo ./sync-digitalarchive <site-name> 
$ sudo ./sync-digitalarchive ALL 
$ sudo ./sync-digitalarchive <site-name> installation
```
-   Type the password for user `daus`
-   Type an option:
    -   `y` to perform a dry run
    -   `Y` to perform the sync
    -   `n` or any other character to exit
-   Press `Enter`

Adding the `installation` argument will also sync:
```
es.ini
bootstrap.php
index.php
error_log
admin/
application/
install/
```

The output is written to `bin/logs/sync-HH-MM-SS.log`

## Server requests

From a terminal:

-   Choose one of these commands:

```
remote-request <request> <site-name>
remote-request <request> ALL

[daus@avantlogic bin]$ ./nightly-cron-job
```

-   Requests:
```
garbage-collection
ping
es-health-check
vocab-update
vocab-rebuild
```

## Common vocabulary updates

To update the common vocabulary:

-   Make changes to one or more of the following files:
    -   `input-translations.csv`
    -   `input-additional-terms.csv`
    -   `input-nomenclature-sortEn_2020-05-18.csv` (replace with latest version from Nomenclature)
-   Run `build_common_facets.py`
-   Test the changes locally and build again until satisifed
-   When done making changes:
    -   Delete local file `input-previous-digital-archive-vocabulary.csv`
    -   Rename local file  `digital-archive-vocabulary.csv` to `input-previous-digital-archive-vocabulary.csv`
    -   Upload `digital-archive-vocabulary.csv` to `digitalarchive.us/public_html/vocabulary`
-   Verify that `digital-archive-diff.csv` file was successfully FTPed to `digitalarchive.us/public_html/vocabulary`
-   Go to the `vocabularly` folder on `digitalarchive.us`
-   Verify that `/vocabulry/data/digital-archive-sites.csv` has the correct site information
-   Run `python3 refresh_common_vocabulary.py`

It is also possible for a developer to simulate a remote update locally via the query string:

``` text
http://localhost/omeka/avant/remote?action=refresh-common&password=ABC123
```

## Omeka updates
Update a Digital Archive site to use a new release of Omeka. Updating involves copying Omeka core files from the release to the site folder. Since the Digital Archive does not modify any Omeka core files, these is no need to review changes to those files. 

### Download the new release
- View the new release of Omeka Classic on [omeka.org](https://omeka.org/classic/download/).
- Download the latest release from the [releases page](https://github.com/omeka/Omeka/releases) on GidHub.
    - The release file will have a name like `omeka-3.0.1.zip`.
- Put the zip file on the desktop or other folder that is not deeply nested. In a deeply nested folder, some files will get an unzip error because their resulting file path is too long.    
- Unzip the release into a work folder named as the release e.g. `omeka-3.0.1`.
- Move the work folder to the `Omeka Releases` folder for safe keeping.
- Delete the zip file.

### Update the local development site

!!! note ""
    Before proceeding, run Omeka on the development site to verify it runs properly with the *current release*. There should be no issues, but if, for example, something in the environment changed that created a problem, find and fix it first so you won't think it's related to the new release.

- Make a backup copy of the current release folder **except for the `files` folder** which is huge.
- Use [Beyond Compare](https://www.scootersoftware.com/) or similar diff tool to compare the current and new release folders.
- Copy (**do not Mirror**) the following **core files** to `C:\xampp\htdocs\omeka`:
```
admin
application
install
plugins/ExhibitBuilder
plugins/SimplePages
themes/default
bootstrap.php
README.md
```

![update files](update-1.jpg)

### Verify that the new release works properly
Normally the site should just come up, though on releases of Omeka prior to 3.0 you were presented with a dialog to update the database. It appears that 3.0 updates the database automatically.

#### Troubleshooting
Past updates of release Omeka 2.* have always gone smoothly, but 3.0 presented problems. When it first came up it reported a Zend_Controller_Exception and then an InvalidArgumentException. The errors appeared to be triggered by a plugin and by AvantTheme, though later there were no issues with either, so it probably had to do with the interim transition from the old to the new release. The solution was to back out the new release, and with the older version running, deactivate all of the Avant plugins and switch from AvantTheme to the default Omeka theme. After updating the site again with the new release, the errors went away and none reoccurred after switching back to AvantTheme and activating the Avant plugins.

## Running scripts

### CRON jobs

### Root privileges
A user with root privileges can run bash scripte that modify files on every Digital Archive installation on the server.

To assign a user root privileges via sudo:
-   Go to WHM and choose `Manage Wheel Groupt Users`
-   Add a user to the wheel group

A user in the `wheel` group can use the system's `su` and `sudo` utilities.

### Making a script executable
Use the `chmod` command to make a script file executable. For example, you can make file `foo` executable with this command:

```
chmod +x foo
```

To execute the `foo` script type:

```
./foo
```

If a script requires root privileges, use `sudo` to run it. For example:

```
sudo ./foo
```

To add a job:
```
crontab -e
```

See [crontab.guru](https://crontab.guru/).

## Increase max execution time

For long running foreground jobs like a reindex, you need to make sure that the PHP max_execution_time
is high enough to let the job complete. The default of 30 seconds is usually too low.

-   Go to cPanel
-   In the Software section choose “Select PHP Version”
-   Click “Switch to PHP Options” at upper right
-   Click the value of  max_execution_time.
-   Enter a new value, click Apply
-   Click Save

## Reset a MySQL table's Auto Increment

See: <https://viralpatel.net/blogs/reseting-mysql-autoincrement-column/>

    ALTER TABLE table_name AUTO_INCREMENT = n;

where n will be the id for the next record created.

---
