# PastPerfect Exporter

The PastPerfect Exporter (PPE) is a software program that exports records PastPerfect and
imports them into the Digital Archive as hybrid items by making HTTP requests to the
[AvantHybrid](/plugins/avanthybrid/) plugin.

---

## What gets exported

The PPE always exports the following columns from PastPerfect's catalog tables:

-	PPID
-	OBJECTID
-	OBJNAME converted to Nomenclature natural order
-	CAT with `A`, `L`, `O`, and `P` changed to `Archives`, `Library`, `Objects`, and `Photos`
-	SUBJECTS
-	TITLE
-	WEBINCLUDE as `1` or `0`

The PPE rejects any records where:

-	WEBINCLUDE is blank unless the `private` config option is `yes`
-	TITLE is blank
-	OBJNAME is blank
-	OBJECTID is blank
-	OBJECTID is not unique

The PPE exports these pseudo columns:

-	IMAGE as a semicolon separated list of the record's image file names
-	THUMB as a semicolon separated list of `IMAGE` values` prefixed by their PPO folder number
-	SITE as the PPO folder containing the source record

The PPE Exports other columns as specified by the `fields` config option.

As example of what the PPE exports is shown below as a JSON string.

``` text
{'PPID': 'B427FDC4-5A2A-42AA-A146-337349578482', 'OBJECTID': '001-056-1-2161',
'OBJNAME': 'Annual Meeting report', 'TITLE': 'Annual Meeting of the Garden Club of America',
'IMAGE': '008/00105612161.jpg', 'THUMB': '008/thumbs/00105612161.jpg', 'WEBINCLUDE': '1',
'SITE': 'archive/<hybrid-id>', 'CAT': 'Archives', 'SUBJECTS': 'Gardens;History',
'DATE': '1934', 'PLACE': '', 'CREATOR': '', 'PUBLISHER': '', 'COLLECTION': '',
'DESCRIP': 'Yellow bound yearbook program with pencil reading Garden Club of Mt. Desert.'}
```

---

## pp_export.config

``` text
[options]
organization = Your organization name goes here
pp5data = \\NAS\PastPerfect\Data
fields =
	DATE
	PLACE
	CREATOR
	PUBLISHER
	COLLECTION
	DESCRIP

[import]
id = mdihs
url = http://yourdomain/digitalarchive/avant/remote
password = rock34XQ

[admin]
bulk = no
catalog = all
details = no
dryrun = no
force = no
limit = 0
private = no
trace = no
```
bulk
:	The `bulk` option should always be set to `no`. The only exception is if you will be exporting
	hundreds or thousands of items and you want to speed up the export process. This would be the
	case for a new installation or when using the `force` option.

	Read about AvantHybrid [bulk import](/plugins/avanthybrid/#bulk-import) feature to understand
	how it works. As noted in that documentation, when you use this option, you'll need to 
	[rebuild your Digital Archive Elasticsearch indexes](/administrator/reindex) when you are done
	importing.

catalog
:	The `catalog` option must be set to either `all` or to one of the PastPerfect catalog names
	`ARCHIVES`, `LIBRARY`, `OBJECTS`, and `PHOTOS`. Any other value will result in an error.

details
:	Set the `details` option to `yes` only if you want to see additional statistics. Currently,
	the only additional statistics is a listing of non-unique OBJECTID values.

dryrun
:	Set the `dryrun` option to `yes` when you want to see what actions PPE will take, but without
	actually calling AvantHybrid to import into the Digital Archive. This is a quick and safe way
	to learn what hybrid items will get added, updated, or deleted in the Digital Archive. When you
	are happy with the actions, set the option to `no`.

force
:	Force should always be set to `no`. The only exception is if for some reason you need to force
	every hybrid item in your Digital Archive to get updated even if it's corresponding PastPerfect
	record has not changed. Se the  See the section below on adding a new export column as an example when
	you might use this option.

limit
:	Limit should normally be set to `0` which means there is no limit on how many source records will
	be exported to the Digital Archive. You can set the limit to a number when you only want to
	export a limited number or records. This option can be combined with the `dryrun` option when you
	are just trying to get a sense of what will get exported without operating on the entire set of
	PastPerfect records.

private
:	The `private` option controls whether PastPerfect records that are not set to be exported to
	PastPerfect Online will get exported to the Digital Archive. Set the option to `yes` to export
	them as non-public Digital Archive hybrid items or set it to `no` to skip them during export.

trace
:	This is a developer option that can be set to `yes` to have AvantHybrid report additional information
	about its response to a request.		

## How it works	

## Adding a new export column

Ideally, you should plan ahead so that your initial export will contain all of the PastPerfect
columns that you want to have appear in the Digital Archive. However, if later you decide you
want to add a column, follow these steps.

-	Add an element for the column in Omeka
-	Add the element to the [Column Mapping](plugins/avanthybrid/#configuration-options)
	option in the AvantHybrid configuration
-	Add the column to the the `fields` option in the `pp_export.config`
-	Set the `force` configuration option to `yes`
-	Set the `bulk` configuration option to `yes`
-	Run the PPE
-	Set the `force` configuration option to `no`
-	Set the `bulk` configuration option to `no`

Assuming that `catalogs` is set to `all` and `limit` is set to `0`, the steps above will
update every hybrid item in the Digital Archive to include the new column. Be aware that
if you have thousands of PastPerfect records, this could take a long time. Also, because
you'll be using the `bulk` option, you'll need to rebuild your Elasticsearch
indexes after the updates finish as explained for the `bulk` option.

## PastPerfect Exporter software

The PPE is implemented as a Python program that was developed by George Soules of AvantLogic Corporation.
It was written for organizations who want to continue using PastPerfect as their primary collections
management software, but also want to share their collections online with other other organizations
that use the Digital Archive for online sharing. It is not intended for use as a PastPerfect migration
tool, nor is is suitable for that purpose since it can only export by making HTTP requests one
record at a time to the Digital Archive's AvantHybrid plugin.
The source code is available upon request as open source for use in non-commercial applications.

The program consists of a single Python script named `export_pp.py` that imports a Python package
named `avant_dbfread` which is a near-exact copy of Ole Martin Bjorndalen's
[dbfread](https://github.com/olemb/dbfread). The only modification is to the `FieldParser.decode_text`
so that it handles a `UnicodeDecodeError` exception without terminating processing. All direct
access to and interpretation of the PastPerfect dBase files is performed by the dbfread logic.

### export_pp.exe

To allow the exporter to run on a Windows computer where PastPerfect is used, without having to have
Python 3 installed on that same computer, `export_pp.py` gets turned into a standalone `.exe`
program using [pyinstaller](https://www.pyinstaller.org). The resulting `export_pp.exe`
file can simply be copied to and run on the Windows computer. It requires no installer and no
changes to the Windows registry.

Follow these steps to create `export_pp.exe`:

-   Go to the folder containing `export_pp.py`
-   Right click and choose `Git Bash Here`
-   Type `pyinstaller --onefile export_pp.py`
-   pyinstaller will create in that folder `\dist\export_pp.exe`
-	Copy `export_pp.config` to the `dist` folder
-	Edit `export_pp.config` if necessary

Follow these steps to run `export_pp.exe`:

-	Open a Windows Command Prompt window
-	CD to the `dist` folder
-	Type `export_pp.exe`

If you don't run the program from a Command Prompt window, it will automatically
open a Command Prompt window to run in, but the window will close when execution ends
and you won't be able to see the results.




