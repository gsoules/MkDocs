# PastPerfect Export

---

## .config file options

```
[options]
organization = Mount Desert Island Historical Society
export = C:\Users\gsoules\Desktop
data = C:\pp5\Data
delete_last_export = no
fields = 
	GPARENT
	PARENT
	DESCRIP
last_export = 2020-03-16 08:06:39
```

## Export data to a CSV file

-   Copy `pp_export.exe` to a PastPerfect computer
-   Edit `pp_export.config` as appropriate for that computer's PastPerfect installation
-   Open a Windows Command Prompt window
-   CD to the folder containing `pp_export.exe`
-   Type `pp_export.exe`

!!! warning "Important"
    If you don't run pp_export from a Command Prompt window, you won't be able to see its output.

### Issues to be resolved

- 	Need GUI interface so exporter does not have to be run in a command window.
-	Need to ensure that the correct export date is used
	-	To avoid case where they export, but don't import, then next export won't contain all updates
	-	Make the first row of the export CSV contain the timestamp of the export
		so that the Digital Archive can record it
	-	Require that admin go to the Digital Archive to learn the last export date
-	Consider having the exporter automatically fetch the last export/import date from the Digital Archive	
-	Change so that all files installed in C:\pp5Export folder
-	Figure out how to detect deletions on the desktop, not by uploading the entire set of ObjectIds to
	the Digital Archive e.g.
	-	On every export, create a file containing only the exported ObjectIds
	-	On the next export, check to see if any records got deleted and then include special
		'DELETE' rows into the export.csv.

## Add or remove exported fields

-   Always export all fields?

## Python

### avant_dbfread

This package is a near-exact copy of Ole Martin Bjorndalen's [dbfread](https://github.com/olemb/dbfread).
The one difference is that `FieldParser.decode_text` now handles a `UnicodeDecodeError` exception.

### Create .exe with pyinstaller

-   Go to `Python\PastPerfect\pp_export\`
-   Right click and choose `Git Bash Here`
-   Type `pyinstaller --onefile pp_export.py`
-   pyinstaller will create  `Python\PastPerfect\pp_export\dist\pp_export.exe`

### Run a Python program from a Command or Bash window

Specify the `-u` option so that console output goes immediately to the window without getting buffered.
Without the option, you won't see any output until the program completes.

```
python -u <filename>.py
```    
