# Creating logs for every event

If we want Wazuh to create logs for every event that happens on the endpoint, we need to make some modification.



## Edit `ossec.conf` in the Wazuh manager

<pre data-title="/var/ossec/etc/ossec.conf" data-overflow="wrap" data-line-numbers><code>    &#x3C;ossec_config>
        &#x3C;global>
--          &#x3C;logall>no&#x3C;/logall>
<strong>++          &#x3C;logall>yes&#x3C;/logall>  
</strong>--          &#x3C;logall_json>no&#x3C;/logall_json>
<strong>++          &#x3C;logall_json>yes&#x3C;/logall_json>
</strong><strong>        &#x3C;/global>
</strong>    &#x3C;/ossec_config>
</code></pre>
