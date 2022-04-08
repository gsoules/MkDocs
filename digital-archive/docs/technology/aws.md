# AWS

## Login in to AWS as the root user

-   Go to <https://signin.aws.amazon.com/>
-   Click the **_Sign In to the Console_** button
-   Choose the **_Root user_** sign in option
-   Enter the root user email address
-   Click the **_Next_** button
-   Enter the root user password
-   Click the **_Sign in_** button
-   On the **_AWS Management Console_** page, find and click on **_Amazon OpenSearch Service_**
-   You'll now be on the **_Amazon OpenSearch Service dashboard_** page

## Access policy

Normally there should be no reason to every modify the  access policy, but here is how to see it.

-   Login in to AWS as the root user
-   Click the `digitalarchive` domain on the **_Amazon OpenSearch Service dashboard_** page
-   Click on the  **Security configuration_** tab


## Kibana

The examples in this section all use `myindex` as the index name.

To use Kibana to view actual JSON for an AvantElasticsearch search, follow the steps to  
[execute Elasticsearch query in Kibana](/technology/php/#execute-elasticsearch-query-in-kibana)


##### Show mappings

``` json
GET /myindex/_mapping/_doc
```

##### Search

This example will return up to 2000 results.

``` json
GET myindex/_search
{ 
  "query": {
    "match_all": {}
  }  , "size": 2000
}
```

This example will return all items where the contributor Id is `swhpl`.

``` json
GET acadia/_search
{
  "query": {
    "terms": {
      "item.contributor-id": [
        "swhpl"
      ]
    }
  }
}
```

##### Delete an index

``` json
DELETE /myindex
```

The response should be

``` json
{
  "acknowledged" : true
}
```
