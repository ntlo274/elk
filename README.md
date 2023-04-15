# elk
elastic search service file
/lib/systemd/system/elasticsearch.service

/etc/elasticsearch/
in this folder we noted 2 files elasticsearch.yml and jvm.options
we can set memory for elastic search in jvm.options, the memory depends on server has
the main configuration for elastic search is on elasticsearch.yml

cluster.name: elastic-search

node.name: node-1

node.roles: [data, master]

path.data: /data

path.logs: /var/log/elasticsearch

network.host: 192.168.1.254

discovery.seed_hosts: ["192.168.1.254", "192.168.1.253", "192.168.1.252"]

cluster.initial_master_nodes: ["192.168.1.254", "192.168.1.253", "192.168.1.252"]

xpack.security.enabled: false

xpack.security.transport.ssl.enabled: false

xpack.security.http.ssl.enabled: false

Hi there, as you have figured out, security features are enabled and configured by default. 
We strongly suggest that you keep it this way so that your data are protected. 
If this doesn't fit your use case and you still want to disable security, you can
Before starting Elasticsearch for the first time
Set xpack.security.enabled: false and then start Elasticsearch
After you have started Elasticsearch for the first time
You have two options here
Set

xpack.security.enabled: false
xpack.security.transport.ssl.enabled: false
xpack.security.http.ssl.enabled: false

and then start Elasticsearch.

Run

bin/elasticsearch-keystore remove xpack.security.transport.ssl.keystore.secure_password

bin/elasticsearch-keystore remove xpack.security.transport.ssl.truststore.secure_password

bin/elasticsearch-keystore remove xpack.security.http.ssl.keystore.secure_password

Set

xpack.security.enabled: false

and then start Elasticsearch.

curl -XGET http://192.168.1.254:9200

curl -XGET http://192.168.1.254:9200/_cluster/health?pretty

