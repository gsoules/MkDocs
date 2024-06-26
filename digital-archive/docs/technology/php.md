# PHP Development

AvantLogic performs PHP development using:

- Windows 11
- [Laragon](https://laragon.org/)
- PHP Storm

[Learn how to set up the environment](#setting-up-a-new-development-environment).

## PhpStorm

### Running the Digital Archive in PHP Storm

This section describes how to edit and debug PHP files.

-   Run the Laragon Control Panel
    - Start All
    - Close or hide the panel

-   Run PhpStorm
    - Open the Digital Archive project: `C:\laragon\www\omeka`

How To:

- Global search of files: `shift-ctrl-f` (press `Esc` to close the panel)
- Run a site in debugging mode: `Run > Debug 'Omeka'`

Syncing:

-   Use [Beyond Compare](/technology/install-digital-archive/#beyond-compare) to sync changes to themes and plugins files.

### Debugging a remote request

Remote requests are normally posted to a production instance of the Digital Archive. For development purposes, a logged-in super user can make GET requests in order to get into the debugger to set breakpoints. This technique is supported by the `AvantAdmin::handleRemoteRequest()` method for URLs like these:

``` text
http://localhost/omeka/avant/remote?id=devb&action=es-health-check&password=XDVIPG
```

``` text
http://localhost/omeka/avant/remote?id=devb&password=rnfeKH1C&action=hybrid-add
```
The first request above is for a remote health check request.

The second request above is for a `hybrid-add` action, but the URL does not contain the data to be added. Because of the nature and length of the data, it's not practical to pass it as query string argument, but you can copy/paste the data you want to test with into the the `$data` variable in method `HybridImport::getSourceRecordData()`.

## Force style.css reload

-   Edit `themes\AvantTheme\common\header.php`
-   Bump `$version` passed to `queue_css_file('style', 'all', false, 'css', $version);`

## Execute Elasticsearch query in Kibana

-   Open `AvantElasticsearchQueryBuilder::constructSearchQuery` in PhpStorm
-   Set a breakpoint on the last line of code `return $params`
-   Perform a search that triggers the breakpoint
-   Copy/paste the value of `$kibana` into the Kibana Dev Tools
-   Use Kibana's Auto Indent to format it

See the [Kibana](/technology/aws/#kibana) section on the AWS page.

## See SQL queries and logging

**To see queries emitted by AvantSearch**

-   Open `SearchQueryBuilder::buildAdvancedSearchQuery` in PhpStorm
-   Set a breakpoint on the last line of code `$sql = (string)$this->select;`
-   Perform a search that triggers the breakpoint
-   Step past the assignment to `$sql`
-   Right click on `$sql` and choose **_Evaluate Expression_**
-   On the **_Evaluate_** dialog enter `(string)$sql`
-   Click the **_Evaluate_** button
-   In MySQL Workbench:
    -   Choose **_File_** > **_New Query Tab_**
    -   Paste the SQL into the empty query window
    -	Click the Beautify/Reformat icon (looks like a wide paint brush)
    -   Shift the text to the left so you can see it

**To see queries emitted by Omeka**

-   Open `AvantSearchPlugin::hookItemsBrowseSql($args)` in PhpStorm
-   See a breakpoint on the call to `buildSearchQuery($args)`
-   Perform a search that triggers the breakpoint
-   Right-click on `$args` and choose **_Evaluate Expression_**
-   In the **_Evaluate_** dialog type `(string)$args["select"]`
-   Click the **_Evaluate_** button
-   Follow the previous set of steps to view the SQL in MySQL Workbench

**To log queries to `errors.log`**

-   Edit `C:\laragon\www\omeka\application\config\config.ini`
-   Set:
    -   `log.sql = true`
    -   `log.priority = Zend_Log::DEBUG`
-	View `C:\laragon\www\omeka-2.5\application\logs\errors.log` in PhpStorm
-   If the file does not always refresh right away:
    -   Click in in the `errors.log` PhpStorm window
    -   Click in the browser window where you are debugging
    -   Come back to PhpStorm where `errors.log` should have refreshed

To see queries as they occur:

-   Open `C:\laragon\www\omeka-2.6\application\libraries\Zend\Db\Select.php`
-   Set a breakpoint on line 1379 where `__toString()` returns the SQL

---

## Setting up a new development environment
Here are some of the trickiest things you need to do when setting up a development environment
on a new computer.

### Install Laragon
-   Download and install Laragon
-   Download the [zip file release of MariaDB](https://dlm.mariadb.com/browse/mariadb_server/163/1957/winx64-packages/) (not the .msi file)
-   Extract the zip to `laragon\bin\mysql`
-   Set Laragon to use MariaDB instead of MySQL by choosing MySQL > Version from the menu
-   In the Laragon menu choose Apache > SSL > Enabled

### Enable XDEBUG to work with PHP Storm:
-   Download and install the appropriate TS version of the [Xdebug](https://xdebug.org/download#releases) dll for Laragon's version of PHP
-   Copy the dll to `laragon\php\php-8.1.10-Win32-vs16-x64\ext`.
-   Configure PHPStorm to use XDebug
-   Add lines similar to those below to the end of `php.ini`:

``` text
[XDebug]
zend_extension = C:\laragon\bin\php\php-8.1.10-Win32-vs16-x64\ext\php_xdebug-3.3.2-8.1-vs16-x86_64.dll
xdebug.remote_enable=1
xdebug.remote_host=localhost
xdebug.remote_port=9000
xdebug.remote_handler=dbgp
xdebug.remote_autostart=0
xdebug.mode=debug
```
Restart Apache after making changes to `php.ini`.

### Install pdftotext
-   Copy the file `pdftotext.exe` from another machine into `c:\laragon`.
-   Add the path `C:\laragon` to your Windows environment variables.
-   Restart the PC to get the path change to take effect.


### Install imagick (Image Magic):
-   See [this article](https://phpandmysql.com/extras/install-imagemagick-and-imagick-xampp)
(the article is for XAMPP but the result works for Laragon)
-   Set Omeka **_ImageMagick DIrectory Path_** to `C:\Program Files\ImageMagick-7.1.0-Q16-HDRI`

---

