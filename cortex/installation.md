# Installation

## Dependencies

{% tabs %}
{% tab title="Debian" %}
{% code overflow="wrap" lineNumbers="true" %}
```
apt install wget gnupg apt-transport-https git ca-certificates ca-certificates-java curl  software-properties-common python3-pip lsb_release
```
{% endcode %}
{% endtab %}

{% tab title="RPM" %}
{% code overflow="wrap" lineNumbers="true" %}
```
yum install pkg-install gnupg chkconfig python3-pip git 
```
{% endcode %}
{% endtab %}
{% endtabs %}



## Java Virtual Machine

### Installation

{% tabs %}
{% tab title="Debian" %}
{% code overflow="wrap" lineNumbers="true" %}
```
apt install -y openjdk-11-jre-headless
echo JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64" >> /etc/environment
export JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"
```
{% endcode %}
{% endtab %}

{% tab title="RPM" %}
{% code overflow="wrap" lineNumbers="true" %}
```
sudo yum install -y java-11-openjdk-headless.x86_64
echo JAVA_HOME="/usr/lib/jvm/jre-1.8.0" | sudo tee -a /etc/environment
export JAVA_HOME="/usr/lib/jvm/jre-1.8.0"
```
{% endcode %}
{% endtab %}
{% endtabs %}



## Elasticsearch

### Installation

{% tabs %}
{% tab title="Debian" %}
{% code overflow="wrap" lineNumbers="true" %}
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch |  sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" |  sudo tee /etc/apt/sources.list.d/elastic-7.x.list 
sudo apt install elasticsearch
```
{% endcode %}
{% endtab %}

{% tab title="RPM" %}

{% endtab %}
{% endtabs %}



## Edit `elasticsearch.yml`

{% code title="/etc/elasticsearch/elasticsearch.yml" overflow="wrap" lineNumbers="true" %}
```
http.host: 127.0.0.1
transport.host: 127.0.0.1
cluster.name: hive
thread_pool.search.queue_size: 100000
path.logs: "/var/log/elasticsearch"
path.data: "/var/lib/elasticsearch"
xpack.security.enabled: false
script.allowed_types: "inline,stored"
```
{% endcode %}



## Cortex

### Installation

{% tabs %}
{% tab title="Debian" %}
{% code overflow="wrap" lineNumbers="true" %}
```
wget -O- "https://raw.githubusercontent.com/TheHive-Project/Cortex/master/PGP-PUBLIC-KEY"  | sudo apt-key add -
wget -qO- https://raw.githubusercontent.com/TheHive-Project/Cortex/master/PGP-PUBLIC-KEY |  sudo gpg --dearmor -o /usr/share/keyrings/thehive-project.gpg
echo 'deb https://deb.thehive-project.org release main' | sudo tee -a /etc/apt/sources.list.d/thehive-project.list
apt install cortex
```
{% endcode %}
{% endtab %}
{% endtabs %}
