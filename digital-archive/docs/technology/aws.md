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

## Modify the access policy

-   Login in to AWS as the root user
-   Click the `digitalarchive` domain on the **_Amazon Elasticsearch Service dashboard_** page
-   Choose **_Modify access policy_** from the **_Actions_** dropdown

Normally, the access policy should be specified as shown below to limit anonymous access
to searching only. For development and debugging purposes, you can *temporarily* remove
`/_search` from the end of the **_Resource_** to allow access from the Kibana developer tools.

``` json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "*"
      },
      "Action": "es:*",
      "Resource": "arn:aws:es:us-east-2:0xxxxxxxxxx8:domain/digitalarchive/*/_search"
    }
  ]
}
```

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
