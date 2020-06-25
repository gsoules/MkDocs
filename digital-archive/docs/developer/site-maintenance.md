# Digital Archive site maintenance

---

## Omeka updates

The Omeka core files are updated by the Omeka team a few times each year.

*Instructions to be added here for applying Omeka updates*

## Plugin and Theme updates

To update the `plugins` and `themes` folders on all Digital Archive sites:

-   Go to cPanel for `digitalarchive.us` and choose `Terminal`
-   `cd bin`
-   `sudo ./sync-digitalarchive`
-   Type the password for user `daus`
-   Type an option:
    -   `y` to perform a dry run
    -   `Y` to perform the sync
    -   `n` or any other character to exit
-   Press `Enter`

![run sync-digitalarchive](site-maintenance-1.jpg)

The output is written to `log.txt`

## Common vocabulary updates

To update the common vocabulary:

-   Make changes to one or more of the following files:
    -   `input-translations.csv`
    -   `input-additional-terms.csv`
    -   `input-nomenclature-sortEn_2020-05-18.csv` (replace with latest version from Nomenclature)
-   Run `build_common_facets.py`
-   Test the changes locally and build again until satisifed
-   When done making changes:
    -   Delete local file `digital-archive-vocabulary.csv`
    -   Rename local file  `output-digital-archive-vocabulary.csv` to `digital-archive-vocabulary.csv`
    -   Upload `digital-archive-vocabulary.csv` to `digitalarchive.us/public_html/vocabulary`
-   Verify that `digital-archive-diff.csv` file was successfully FTPed to `digitalarchive.us/public_html/vocabulary`
-   Go to `digitalarchive.us/python/vocabulary`
-   Verify that `digitalarchive.us/python/vocabulary/data/digital-archive-sites.csv` has the correct site information
-   Run `python3 refresh_common_vocabulary.py`


## Running scripts

### Root privlidges
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

To execuate the `foo` script type:

```
./foo
```

If a script requires root privileges, use `sudo` to run it. For example:

```
sudo ./foo
```
