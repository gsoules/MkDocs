# PHP Development

## Update local DB

-   Goto to phpAdmin on server
-   Truncate session table
-   Export SQL
-   Go to phpAdmin on localhost
-   Create a new DB with today's date in the name
-   Run MySQL Workbench
-   Double click on name of new DB 
-   Import SQL into new DB
-   Change db.ini to new DB name
-   Change Navigation landing page to localhost URL
-   Go to AvantElasticsearch config and change site to `deva`
-   Reindex
    -   Export all into deva
    -   Import into new deva
    -   Delate all from devshr
    -   Import into existing devshr
-   Get latest files from server (just ones added/changed since date of last DB)
