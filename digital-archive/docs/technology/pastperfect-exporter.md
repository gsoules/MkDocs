# PastPerfect Exporter

The PastPerfect Exporter (PPE) is a software program that exports records from the dBase tables
used by PastPerfect into a file suitable for import into the Digital Archive using the 
[AvantHybrid](/plugins/avanthybrid/) plugin.

---

Always exports:

PPID
OBJECTID never blanks or duplicates
CAT as one of the four PP names
OBJNAME translated to CV natural order, never non-nomenclature
SUBJECTS as-is
TITLE
IMAGE
THUMB
WEBINCLUDE as 1 or 0
SITE end of the path for the record

---

## Exporter software

### .config file options

```
[options]
organization = Your Historical Society
export = C:\xampp\htdocs\omeka\files\hybrid
data = C:\pp5\Data
delete_last_export = no
fields = 
	DATE
	PLACE
	CREATOR
	PUBLISHER
	COLLECTION
	DESCRIP
last_export = 2020-09-05 10:10:15

[ftp]
enabled = yes
host = ftp.yourdomain.net
user = hybrid@yourdomain.net
password = kxxxxxxxxx9

[import]
site = yrsite
url = http://yourdomain/digitalarchive
password = abcd1234
```

### Add an export column

-	Add an element for the column in Omeka
-	Add to column mapping in AvantHybrid configuration
-	Add the column to the .config file above
-	Export all records and import them

### Export data to a CSV file

-   Copy `export_pp.exe` to the local computer
-   Edit `export_pp.config` as appropriate for that computer's PastPerfect installation
-   Open a Windows Command Prompt window
-   CD to the folder containing `export_pp.exe`
-   Type `export_pp.exe`

!!! note ""
    If you don't run export_pp from a Command Prompt window, you won't be able to see its output.

### Python

#### avant_dbfread

This package is a near-exact copy of Ole Martin Bjorndalen's [dbfread](https://github.com/olemb/dbfread).
The one difference is that `FieldParser.decode_text` now handles a `UnicodeDecodeError` exception.

#### Create .exe with pyinstaller

-   Go to `Python\PastPerfect\export_pp\`
-   Right click and choose `Git Bash Here`
-   Type `pyinstaller --onefile export_pp.py`
-   pyinstaller will create  `Python\PastPerfect\export_pp\dist\export_pp.exe`

#### Build a .exe with pyinstaller

-   Go to `Python\PastPerfect\export_pp\`
-   Right click and choose `Git Bash Here`
-   Type `pyinstaller --onefile export_pp.py`
-   pyinstaller will create  `Python\PastPerfect\export_pp\dist\export_pp.exe`

#### Run a Python program from a Command or Bash window

Specify the `-u` option so that console output goes immediately to the window without getting buffered.
Without the option, you won't see any output until the program completes.

```
python -u <filename>.py
```    
