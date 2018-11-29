# Description

This role configures a single [ElasticSearch](https://www.elastic.co/guide/en/elasticsearch/reference/6.3/index.html) instance which acts as a Load Balancer for use by [Kibana](../kibana). It connects to the existing ElasticSearch cluster configured in the [elasticsearch](../elasticsearch) role and is used by the locally running Kibana.

# Configuration

This is optional, but you can enable public access to the Load Balancer:
```yaml
es_lb_public: true
es_lb_domain: 'es.example.com'
es_lb_username: 'search-user'
es_lb_password: 'very-secret-password'
```

# Details

The main difference is the fact that most normal ElasticSearch functionalities are disabled on this node via the following configuration in [`templates/elasticsearch.tml.j2`](./templates/elasticsearch.tml.j2):
```
node.master: false
node.data: false
node.ingest: false
```
