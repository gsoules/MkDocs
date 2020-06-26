
# Bulk site installation

---

-   Create a database on the server.
-   Copy and extract digitalarchive.zip into public_html
 -   Edit `db.ini` to point to the new database
-   In MySQL Workbench, import generic SQL
    -   File > Open SQL Script
    -   Edit:
        -   org name
        -   org copyright
        -   item type
        -   AWS credentials
-   Assign new PW to super user
-   Set import configuration
-   Import data
-   Rebuild the local vocabulary. If you don't do this before indexing (next step) the terms in the imported
    items will get marked as UNTRACKED.
-   Go to Elasticsearch page
    -   Export all items
    -   Import into new local index
    -   Import into existing shared index

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
