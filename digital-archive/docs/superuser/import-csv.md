# Import CSV data

## Install CSVImportPlus and create Import folder
-	Be sure you have installed and configured ArchiveRepertory 
-	Be sure you have added elements for every column to be imported
-	Install the version of CSVImportPlus v2.3.3 modified by George Soules. This version looks for image files in the /files/import folder and does not require a full pathname in the CSV file.
-	Configure:
    -	Roles: Super
    -	Slow: 0
    -	Repeat: 100
-	Create an import folder in the Omeka installation’s files folder.

---

## Import Data from Excel
-	Upload all of the to-be-imported image and PDF files into the import folder
-	Data preparation
-	Save the Excel file as CSV, but first, avoid  #### in cells by changing the format of all columns to General.
-	Watch out for Excel converting date text to actual dates with the wrong format.
-	Make sure there is a column Item Type that is populated with the installation’s item type e.g. GCIHS. If this column is missing, then choose the default Item Type from the Default Values section of the import screen.
-	Importing:
-	Name the column headers using Element syntax e.g.
    -	Dublin Core:Title
    -	Item Type Metadata:Notes
    -	Item Type
    -	Public
    -	Files
-	Test with a CSV file contains just one or two rows.
-	Step 1:
    -	Click CSV Import+ in the left menu
    -	Click the Browse button and select the text CSV file
    -	CSV format:
        -	Column delimiter: comma
        -	Enclosure: “ (double quote0
        -	Element delimiter: empty
        -	Tag delimiter: comma
        -	File delimiter: comma
    -	Default values:
            -	Item type:   No default item type (if the import file has an Item Type column, otherwise, choose the item type from the dropdown list)
            -	Collection: No default collection
            -	Make records public: Unchecked
            -	Feature records: Unchecked
            -	Elements are html: Unchecked
    -	Process
        -	Identifier field: Identifier
        -	Action:  No default action
        -	Contains extra data: Perhaps, so the mapping...
-	Step 2:
    -	Click the Next button
    -	Verify that the mappings are correct
    -	Verify that the special values are correct:
        -	Identifier should be set to Identifier
        -	Item Type should be set to Item Type
        -	Public should be set to Public
        -	Files should be set to Files
    -	Click the Import CSV file button
    -	Verify that the import worked correctly
    -	If you get the error “The configured PHP path (/usr/bin/php) does not point to a PHP-CLI binary” edit application\config.ini and set background.php.path = "/usr/bin/php-cli"
    -	If the import Completed, but records were skipped, click on the import date/log to see what happened.
-	Import all of the data
    -	Note that certain characters e.g. … (a single character representing an ellipsis) or an accented character like é can cause a mySQL error. When you find one, do a global replace in the CSV file to correct it everywhere.
-	Method  1:
    -	Break the CSV file into chunks of 100 or 200 rows and import the individual files one at a time.
    -	After each import, if any records were skipped, look at the import log to identify and resolve the problem.
-	Method 2:
    -	Attempt to import the entire CSV file.
    -	As errors are encountered:
        o	Fix the offending row in the CSV using Notepad++ or TextPad
        o	Delete all of the good rows above it except for the header row
        o	Save the CSV with a new file name
        o	Try again and repeat until all rows imported.
    -	This method can be the only option if there is a column with dates that Excel insists on converting when you save the CSV file. By working with a text editor like Notepad++ you avoid the conversion problem.
    -	Done

---

## Remove stuff used for import but no longer needed
-	CSV Import+ plugin
-	/file/import folder

