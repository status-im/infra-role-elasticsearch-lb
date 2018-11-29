# Description

This role configures a single [ElasticSearch](https://www.elastic.co/guide/en/elasticsearch/reference/6.3/index.html) instance which acts as a Load Balancer for use by [Kibana](../kibana). It connects to the existing ElasticSearch cluster configured in the [elasticsearch](../elasticsearch) role and is used by the locally running Kibana.

# Configuration

The main difference is the fact that most normal ElasticSearch functionalities are disabled on this node via the following configuration in [`templates/elasticsearch.tml.j2`](./templates/elasticsearch.tml.j2):
```
node.master: false
node.data: false
node.ingest: false
```
