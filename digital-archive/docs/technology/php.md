# PHP Development

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

-   Edit `C:\xampp\htdocs\omeka\application\config\config.ini`
-   Set:
    -   `log.sql = true`
    -   `log.priority = Zend_Log::DEBUG`
-	View `C:\xampp\htdocs\omeka-2.5\application\logs\errors.log` in PhpStorm
-   If the file does not always refresh right away:
    -   Click in in the `errors.log` PhpStorm window
    -   Click in the browser window where you are debugging
    -   Come back to PhpStorm where `errors.log` should have refreshed

To see queries as they occur:

-   Open `C:\xampp\htdocs\omeka-2.6\application\libraries\Zend\Db\Select.php`
-   Set a breakpoint on line 1379 where `__toString()` returns the SQL


---
