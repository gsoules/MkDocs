
# Bulk site installation

---
## Bulk site installation

-   Create a database
-   In MySQL Workbench, import generic SQL
    - Edit:
        - org name
        - org copyright
        - item type
        - AWS credentials
-   Copy digitalarchive.zip into public_html
-   Edit:
    -   `db.ini` to point to the new database
-   Add site name and URL to AvantTheme configuration
-   Assign new PW to users
-   Add/remove item elements
-   Set private elements
-   Site styling and navigation
-   Build vocabulary tables
-   Set import configuration
-   Import data
-   Rebuild the local vocabulary. If you don't do this before indexing (next step) the terms in the imported
    items will get marked as UNTRACKED.
-   Go to Elasticsearch page
    -   Export all items
    -   Import into new local index
    -   Import into existing shared index

!!! warning
    Plugins like AvantRelationships and AvantVocabularies and others won't have their install handlers
    called. Will need to uninstall/install to execute that code.

[AvantAdmin]:         ../../plugins/avantadmin
[AvantCommon]:        ../../plugins/avantcommon
[AvantCustom]:        ../../plugins/avantcustom
[AvantDPLA]:          ../../plugins/avantdpla
[AvantElements]:      ../../plugins/avantelements
[AvantElasticsearch]: ../../plugins/avantelasticsearch
[AvantRelationships]: ../../plugins/avantrelationships
[AvantSearch]:        ../../plugins/avantsearch
[AvantS3]:            ../../plugins/avants3
[AvantZoom]:          ../../plugins/avantzoom
[AvantVocabulary]:    ../../plugins/avantvocabulary
[cPanel]:             web-host.md#cpanel
