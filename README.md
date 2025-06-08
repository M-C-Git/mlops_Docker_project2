Project Summary
===============
This project implements a centralized log management system using the `ELK Stack (Elasticsearch, Logstash, Kibana)`. Logs from multiple sources are collected by `Logstash`, processed, and forwarded to an `Elasticsearch` cluster for indexing and storage. The stored logs are then visualized through `Kibana`, allowing users to search, analyze, and monitor log data in real time via a web interface. This setup improves observability, troubleshooting, and system monitoring across distributed systems.

Porject Diagram
===============
```text
   [logs]     [logs]     [logs]
     |           |          |
   (5000)      (5000)     (5000)
     |           |          |
 +--------+ +--------+ +--------+
 |Logstash| |Logstash| |Logstash|      <<-- Log Shipping
 +--------+ +--------+ +--------+
     \         |         /
        \      |      /
           +--------+
           |Elastic |
           |Search  |                 <<-- Log Storage
           | Cluster|
           +--------+
                |
             (9200)
                |
           +--------+
           | Kibana |                 <<-- Log Visualization
           +--------+
             (5601)
```

Porject Components
==================
1. Log Shipping
* Logstash processes and ships logs from different sources.
* Each Logstash instance listens on port 5000 and pulls log data from corresponding log files or agents.
</br>

2. Log Storage
* Logs are sent to Elasticsearch (ES), a search engine and analytics engine.
* Elasticsearch nodes form a cluster to index and store logs.
* Logstash sends data to Elasticsearch via port 9200.
</br>

3. Log Visualization
* Kibana is the frontend visualization tool for Elasticsearch.
* Connects to Elasticsearch over port 9200.
* Users interact with Kibana through port 5601.