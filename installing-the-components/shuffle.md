# Shuffle

Shuffle is a SOAR tool which allows users to automate their SOC processes.

If you are going the Cloud route, you can use Shuffle's cloud platform.

Since we are using virtual machines, for this lab we will have to install Shuffle on one of those machines.



## Installation

We can install Shuffle using the following commands:

{% code overflow="wrap" lineNumbers="true" %}
```
cd /opt
git clone https://github.com/Shuffle/Shuffle
cd Shuffle
mkdir shuffle-database
sudo chown -R 1000:1000 shuffle-database
sudo useradd opensearch
```
{% endcode %}



## Configuration

We now have to configure Shuffle to run on our machine.

### Edit `docker-compose.yml`

<pre data-title="/opt/Shuffle/docker-compose.yml" data-overflow="wrap" data-line-numbers><code>    ports:
--    - 9200:9200
<strong>++    - 9205:9205
</strong></code></pre>

### Run Shuffle

```
docker-compose up -d
```



## Dashboard

We can now access Shuffle's dashboard at:

```
http://(shuffle-server-ip):3001
```
