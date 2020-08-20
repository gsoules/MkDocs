# PHP Development

## Update local DB

Follow these steps to copy a production database to use for testing on a local
development server.

-   Go to to phpAdmin on the server
-   Truncate the session table
-   Export SQL
-   Go to phpAdmin on localhost
-   Create a new DB with today's date in the name
-   Run MySQL Workbench
-   Double click on name of the new DB 
-   Import SQL into then new DB
-   Change db.ini to use new DB name
-   Change the Navigation landing page to the localhost URL
-   Go to AvantElasticsearch config and change site to `deva`
-   Reindex
    -   Export all into deva
    -   Import into new deva
    -   Import into existing devshr
-   Get latest files from server (just ones added/changed since date of last DB)

## See Elasticsearch query in Kibana

-   Open `AvantElasticsearchQueryBuilder::constructSearchQuery` in PhpStorm
-   Set a breakpoint on the last line of code `return $params`
-   Perform a search that triggers the breakpoint
-   Copy/paste the value of `$kibana` into the Kibana Dev Tools
-   Use Kibana's Auto Indent to format it

For query score analysis: `GET index-name/_search/?explain=true`

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
