# Index API

* How do we create an index?
* An index will be created lazily by ElasticSeach when we post a document:
  ```
  curl -XPOST localhost:9200/orders/_doc/1 \
  -H 'content-type: application/json' \
  -d '{"id": "1", "placedOn": "2016-10-17T13:03:30.830Z"}'
  ```
* To retrieve the document just posted:
* `curl 'localhost:9200/orders/_search?pretty=true'`
* Expected result:

```
{
  "took" : 0,
  "timed_out" : false,
  "_shards" : {
    "total" : 5,
    "successful" : 5,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : 1,
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "orders",
        "_type" : "_doc",
        "_id" : "1",
        "_score" : 1.0,
        "_source" : {
          "id" : "1",
          "placedOn" : "2016-10-17T13:03:30.830Z"
        }
      }
    ]
  }
}
```



