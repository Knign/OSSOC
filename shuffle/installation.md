# Installation



In order to run TheHive on Ubuntu LTS 22.04 machine, we need to install the dependencies.

## Installation

### Dependencies

{% code overflow="wrap" lineNumbers="true" %}
```
apt install wget gnupg apt-transport-https git ca-certificates ca-certificates-java curl  software-properties-common python3-pip lsb-release
```
{% endcode %}

### Java

{% code overflow="wrap" lineNumbers="true" %}
```
wget -qO- https://apt.corretto.aws/corretto.key | sudo gpg --dearmor  -o /usr/share/keyrings/corretto.gpg
echo "deb [signed-by=/usr/share/keyrings/corretto.gpg] https://apt.corretto.aws stable main" |  sudo tee -a /etc/apt/sources.list.d/corretto.sources.list
sudo apt update
sudo apt install java-common java-11-amazon-corretto-jdk
echo JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto" | sudo tee -a /etc/environment 
export JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto"
```
{% endcode %}

### Cassandra

{% code overflow="wrap" lineNumbers="true" %}
```
wget -qO -  https://downloads.apache.org/cassandra/KEYS | sudo gpg --dearmor  -o /usr/share/keyrings/cassandra-archive.gpg
echo "deb [signed-by=/usr/share/keyrings/cassandra-archive.gpg] https://debian.cassandra.apache.org 40x main" |  sudo tee -a /etc/apt/sources.list.d/cassandra.sources.list
sudo apt update
sudo apt install cassandra
```
{% endcode %}

### Elasticsearch

{% code overflow="wrap" lineNumbers="true" %}
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch |  sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
sudo apt-get install apt-transport-https
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" |  sudo tee /etc/apt/sources.list.d/elastic-7.x.list
sudo apt update
sudo apt install elasticsearch
```
{% endcode %}



Now we are all set to install TheHive.

### TheHive

{% code overflow="wrap" lineNumbers="true" %}
```
wget -O- https://archives.strangebee.com/keys/strangebee.gpg | sudo gpg --dearmor -o /usr/share/keyrings/strangebee-archive-keyring.gpg
echo 'deb [signed-by=/usr/share/keyrings/strangebee-archive-keyring.gpg] https://deb.strangebee.com thehive-5.2 main' | sudo tee -a /etc/apt/sources.list.d/strangebee.list
sudo apt-get update
sudo apt-get install -y thehive
```
{% endcode %}



## Cassandra configuration

### Edit `cassandra.yaml`

First we need to edit the configuration file for Cassandra by making the following changes.&#x20;

<pre data-title="/etc/cassandra/cassandra.yml" data-overflow="wrap" data-line-numbers><code>--  cluster_name: 'Test Cluster'
<strong>++  cluster_name: 'OSSOC'
</strong>
--  listen_address: localhost
<strong>++  listen_address: (Ubuntu machine's IP address)
</strong>
--  rpc_address: localhost
<strong>++  rpc_address: (Ubuntu machine's IP address)
</strong>
    seed_provider: 
        parameters:
--          seeds: "127.0.0.1:7000"
<strong>++          seeds: "(Ubuntu machine's IP address):7000"
</strong></code></pre>

Perform the following steps next:

### Stop `cassandra.service`

{% code overflow="wrap" lineNumbers="true" %}
```bash
systemctl stop cassandra.service
```
{% endcode %}

### Remove the old files

{% code overflow="wrap" lineNumbers="true" %}
```
rm -rf /var/lib/cassandra/*
```
{% endcode %}

### Start `cassandra.service`

{% code overflow="wrap" lineNumbers="true" %}
```
systemctl start cassandra.service
```
{% endcode %}

### Check `cassandra.service` status

{% code overflow="wrap" lineNumbers="true" %}
```
systemctl status cassandra.service
```
{% endcode %}



## Elasticsearch configuration

### Edit `elasticsearch.yml`

<pre data-title="/etc/elasticsearch/elasticsearch.yml" data-overflow="wrap" data-line-numbers><code>--  #cluster.name: my-application
<strong>++  cluster.name: ossoc
</strong> 
--  #node.name: node-1
<strong>++  node.name: node-1
</strong> 
--  #network.host: 192.18.0.1   
<strong>++  network.host: (Ubuntu machine's IP address)
</strong>   
--  #http.port: 9200 
<strong>++  http.port: 9200
</strong>    
--  #cluster.initial_master_nodes: ["node-1", "node-2"]
<strong>++  cluster.initial_master_nodes: ["node-1"]
</strong></code></pre>

### Start `elasticsearch`

{% code overflow="wrap" lineNumbers="true" %}
```
systemctl start elasticsearch
```
{% endcode %}

### Enable `elasticsearch`

{% code overflow="wrap" lineNumbers="true" %}
```
systemctl enable elasticsearch
```
{% endcode %}

### Check `elasticsearch.service` status

<pre data-overflow="wrap" data-line-numbers><code><strong>systemctl status elasticsearch.service
</strong></code></pre>



## TheHive configuration

### Change ownership of `/opt/thp` to `thehive:thehive`

{% code overflow="wrap" lineNumbers="true" %}
```
chown -R thehive:thehive /opt/thp
```
{% endcode %}

### Edit `application.conf`

<pre data-title="/etc/thehive/application.conf" data-overflow="wrap" data-line-numbers><code>    db.janusgraph {
        storage {
--          hostname = ["127.0.0.1"]
<strong>++          hostname = ["(Ubuntu machine's IP address)"]
</strong>            cql {
--              cluster-name = thp
<strong>++              cluster-name = ossoc
</strong>            }
        }
        index.search {
--          hostname = ["127.0.0.1"]
<strong>++          hostname = ["(Ubuntu machine's IP address)"]
</strong>        }
    }
    
--  application.baseUrl = "http://localhost:9000"
<strong>++  application.baseUrl = "http://(Ubuntu machine's IP address):9000"
</strong></code></pre>

### Start `thehive`

{% code overflow="wrap" lineNumbers="true" %}
```
systemctl start thehive
```
{% endcode %}

### Enable `thehive`

{% code overflow="wrap" lineNumbers="true" %}
```
systemctl enable thehive
```
{% endcode %}

### Check `thehive` status

{% code overflow="wrap" lineNumbers="true" %}
```
systemctl status thehive
```
{% endcode %}



## Dashboard

We can now access TheHive's dashboard at:

```
## URI: 
http://(Ubuntu machine's IP address):9000
```

### Login credentials

| Username            | Password |
| ------------------- | -------- |
| admin@thehive.local | secret   |
