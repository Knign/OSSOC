# With Shuffle

In order to integrate Wazuh with Shuffle, add the following tag to the `/var/ossec/etc/ossec.conf` file.

<pre data-title="/var/ossec/etc/ossec.conf" data-line-numbers><code><strong>++  &#x3C;integration>
</strong><strong>++    &#x3C;name>shuffle&#x3C;/name>
</strong><strong>++    &#x3C;hook_url>http://&#x3C;YOUR_SHUFFLE_URL>/api/v1/hooks/&#x3C;HOOK_ID>&#x3C;/hook_url>
</strong><strong>++    &#x3C;level>3&#x3C;/level>
</strong><strong>++    &#x3C;alert_format>json&#x3C;/alert_format>
</strong><strong>++  &#x3C;/integration>
</strong></code></pre>
