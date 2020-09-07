# dBase Export

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

-   Copy `pp_export.exe` to the local computer
-   Edit `pp_export.config` as appropriate for that computer's PastPerfect installation
-   Open a Windows Command Prompt window
-   CD to the folder containing `pp_export.exe`
-   Type `pp_export.exe`

!!! warning "Important"
    If you don't run pp_export from a Command Prompt window, you won't be able to see its output.

## Python

### avant_dbfread

This package is a near-exact copy of Ole Martin Bjorndalen's [dbfread](https://github.com/olemb/dbfread).
The one difference is that `FieldParser.decode_text` now handles a `UnicodeDecodeError` exception.

### Create .exe with pyinstaller

-   Go to `Python\PastPerfect\pp_export\`
-   Right click and choose `Git Bash Here`
-   Type `pyinstaller --onefile pp_export.py`
-   pyinstaller will create  `Python\PastPerfect\pp_export\dist\pp_export.exe`

### Build a .exe with pyinstaller

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
