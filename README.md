# Description

This role configures a single [ElasticSearch](https://www.elastic.co/guide/en/elasticsearch/reference/6.3/index.html) instance which acts as a Load Balancer for use by [Kibana](../kibana). It connects to the existing ElasticSearch cluster configured in the [elasticsearch](../elasticsearch) role and is used by the locally running Kibana.

# Configuration

The only mandatory setting is what host to connect to:
```yaml
es_lb_cluster_name: example-es-cluster
es_lb_master_nodes:
  - { name: node-01.es.example.vpn, addr: 1.2.3.4, port: 9300 }
  - { name: node-02.es.example.vpn, addr: 2.3.4.5, port: 9300 }
  - { name: node-03.es.example.vpn, addr: 3.4.5.6, port: 9300 }
```

# Details

The main difference is the fact that most normal ElasticSearch functionalities are disabled on this node via the following configuration in [`templates/elasticsearch.tml.j2`](./templates/elasticsearch.tml.j2):
```
node.master: false
node.data: false
node.ingest: false
```
