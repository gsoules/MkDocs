# Import CSV data

You can import data into the Digital Archive to create or update items from metadata in a CSV file.
You can also import files to be attached to an imported item.

!!! warning "Caution"
    Importing from a CSV file involves many steps and requires the ability to
    use FTP to upload files to the server. You should only attempt to import after carefully
    reading all of the instructions on this page. Be sure you are comfortable with the process
    *before* you begin.

---

## Prerequisites

To import CSV data:

-   The [AvantImport] plugin must be installed and activated
-   The [AvantElasticsearch] plugin must installed, but be *deactivated*
-   You must be logged into Omeka as a super user

## Preparation

Read this section carefully before attempting to import a CSV file.

### Configuration

You must configure AvantImport to tell it which columns from the CSV file that you want to import (source column names)
and what the corresponding Omeka element names are for each column (target column names). It's okay if the CSV file
has column that you don't want to import.

Follow these steps to configure the import:

-	Go to the Omeka `Plugins` page
-	Click the `Configure` button for `AvantImport`
-   In the `Mappings` field, provide a list of source/target column pairs, separated by a colon, as shown in the screenshot below. 
-   Click the `Save Changes` button.

![importing files](import-csv-3.jpg)

### Importing image files

If you will be importing files to be attached to imported items, upload all of the files into the
`digitalarchive/files/import` folder using FTP. In the CSV column used to specify the files, you'll specify just
the file name (with no path) and AvantImport will look for the files in the `import` folder.

To indicate that a CSV column contains a file name, or a semicolon-separated list of file names, use the
pseudo-element name `<files>` in the **Mappings** field on the AvantImport configuration page. In the
screenshot above, the CSV `Images` column will contain file names.

### CSV file syntax

The CSV file must adhere to the following:

-   The CSV file must have UTF-8 encoding as explained in the next section.
-   The first row must contain the source column names used in the configuration above
-   Cells that contain multiple values for a single element must use a semicolon as the value delimeter.
    For example, if an item has three subjects "one", "two" and "three", its Subject cell would contain `one;two;three`.
   
### UTF-8 encoding

AvantImport will only import a CSV file that has [UTF-8](https://en.wikipedia.org/wiki/UTF-8) encoding.
This is to ensure that text containing non-ASCII characters, like the the `é` in `Hébert` will import
without triggering an error when saved by Omeka to the MySQL database.

When saving an Excel file as CSV, choose the `CSV UTF-8` option as shown below.

![UTF-8 format](import-csv-1.jpg)

If working with CSV in a text editor like Notepad++, be sure that the file's encoding is set to UTF-8-BOM
as shown below. The file must have the BOM (Byte Order Mark) in order for AvantImport to recognize it as UTF-8.
Excel will insert the BOM when you choose the option shown above.

![UTF-8 format](import-csv-2.jpg)

If creating a CSV file using Python, use the `utf-8-sig` encoding.

### Excel issues

CSV data often originates in Excel. Verify that the resulting CSV file does not suffer from these issues.

-   Make sure that no cells contain `#######` due to a formatting problem in Excel. If you see this in the
    CSV data, go back to Excel and change the format of all columns to General.
-	If the CSV contains a column containing dates, verify that the date format looks correct. Excel is
    notorious for changing dates to a different format, and for displaying dates differently than they
    actually exist in the CSV file.
-   If Excel insists on converting dates improperly when you save the Excel as a CSV file, your only
    recourse may be to work with the data in a text editor like Notepad++ which is more well-behaved.

!!! note "Suggestion"
    Before attempting to import all of your data, create a test CSV file that contains only two or three rows of CSV data. Use this file to perform all the steps on this page. Only import a file containing all of your data after achieving success with the test file. 

## Import steps

To import from a CSV file:

-   Deactivate the AvantElasticsearch plugin
-   Click `Import CSV File` in Omeka's left admin menu
-   The `Step 1` page will appear

### Choose the import file

On the `Step 1` page:

-	Click the `Browse` button and choose a UTF-8 encoded CSV file to import
-   Check the `Make items public` checkbox if you want the imported items to be public
-	Click the `Next` button
-   The `Step 2` page will appear

![UTF-8 format](import-csv-4.jpg)

### Verify the field mappings
On the Step 2 page:

-   Verify that the mappings are correct. To change the mappings, see [Configuration](#configuration) above.
-   Click the `Import CSV file` button
-   The `Status` page will appear and the import will begin
-   Refresh the browser every so often until the status is `Completed`

![UTF-8 format](import-csv-5.jpg)

### Verify that the import worked correctly

The screenshot below shows that the import completed, but three records were skipped.

![Status page showing statistics](import-csv-7.jpg)

Click on the import date/log to see why the records were skipped. The import log appears showing details
about the import process. The 4th row on the next screen shot shows that one of the file names in the CSV file was not
readable or does not exist. The 5th rows says that the record on row #121 was skipped.

![Log page showing error](import-csv-8.jpg)

The row # in the message is the row number in the CSV file. For example, row #1 is the header row in the
CSV file and row #2 is the first item to be imported.

To import the skipped rows:

-   Determine the cause of the problem. Often it's a mispelling of a file name, or even a difference in letter
    casing. For example, if the CSV file refers to a file named `1234.jpg`, but the actual file name is
    `1234.JPG`, the file won't be found.
-   Make a copy of the import file with all the rows removed except the offending row(s). A good way to do this is to
    use a color to highlight the bad rows, then delete all the rows except for the highlighted ones. If you
    simply start deleting the good rows, the row numbers in the error report will no longer match the rows in the
    CSV file.
-   Fix the row data and/or the file name
-   Reimport the copy of the import file that contains only the skipped rows
-   Repeat this process as necessary until all the data is imported.

### Rebuild the local vocabulary table

Because the import occurs with [Elasticsearch](/glossary/#elasticsearch) disabled, which in turn disables the
[Common Vocabulary](/glossary/#common-vocabulary) feature, you need to rebuild the vocabulary tables.

-   Activate the AvantElasticsearch plugin
-   Choose `Vocabulary Editor` from the left admin menu
-   Click the `Rebuild Local Terms table` button
-   Click `OK` on the confirmation dialog
-   When the build completes, refresh the page to see the updated local terms

!!! note
    You must rebuild the local terms table before rebulding the Elasticsearch indexes.
    If you reindex first, you'll see `UNTRACKED` in the facets panel on any new terms that came
    from the import that were not already in the vocabulary.

### Rebuild the Elasticsearch indexes

Because the import occurs with [Elasticsearch](/glossary/#elasticsearch) disabled, you need to rebuild
the site's Elasticsearch indexes.

-   Choose `Elasticsearch` from the left admin menu
-   Choose the `Export all items from Omeka` radio button
-   Click the `Start` button
-   Choose the `Import into existing local index` radio button *(see important note below)*
-   Click the `Start` button
-   Choose the `Import into existing shared index` radio button
-   Click the `Start` button

!!! warning "Important"
    If the import is being used to bring data into a site that has no items and has never been indexed,
    you must choose `Import into new local index` instead of `Import into existing local index`. To enable
    that option, add the following line to the site's `es.config` file: `new_local_index_allowed = true`  
    This is necessary to properly set the data types for the local index. 

## Cleanup the import folder
Once the import is successful, use FTP to delete the files from the `digitalarchive/files/import`
folder on the server.


[AvantAdmin]:         ../../plugins/avantadmin
[AvantCommon]:        ../../plugins/avantcommon
[AvantCustom]:        ../../plugins/avantcustom
[AvantDPLA]:          ../../plugins/avantdpla
[AvantElements]:      ../../plugins/avantelements
[AvantElasticsearch]: ../../plugins/avantelasticsearch
[AvantImport]:        ../../plugins/avantimport
[AvantRelationships]: ../../plugins/avantrelationships
[AvantSearch]:        ../../plugins/avantsearch
[AvantS3]:            ../../plugins/avants3
[AvantZoom]:          ../../plugins/avantzoom
[AvantVocabulary]:    ../../plugins/avantvocabulary
[cPanel]:             web-host.md#cpanel
