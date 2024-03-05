# Wazuh rule

The custom rule would look as follows:

```
  <rule id="100002" level="10">
    <if_group>sysmon_event1</if_group>
    <field name="win.eventdata.originalFileName" type="pcre2">(?i)mimikatz\.exe</field>
    <description>Mimikatz usage detected.</description>
    <mitre>
      <id>T1003</id>
    </mitre>
  </rule>    
```

1. `<rule id="100002" level="10">`: This is the rule definition with an ID of 100002 and a severity level of 10.
2. `<if_group>sysmon_event1</if_group>`: This specifies the condition or event group that triggers the rule. In this case, it's "sysmon\_event1."
3. `<field name="win.eventdata.originalFileName" type="pcre2">(?i)mimikatz\.exe</field>`: This part defines a condition on a specific field in the event data. It checks if the original file name in the Windows event data matches the regular expression "(?i)mimikatz.exe" case-insensitively.
   * `name="win.eventdata.originalFileName"`: Specifies the field to check.
   * `type="pcre2"`: Indicates the type of regular expression used.
   * `(?i)mimikatz\.exe`: The actual regular expression to match against the original file name.
4. `<description>Mimikatz usage detected.</description>`: Provides a human-readable description of what the rule is checking for. In this case, it states that the rule is detecting the usage of Mimikatz.
5. `<mitre><id>T1003</id></mitre>`: Associates the rule with a specific MITRE ATT\&CK technique ID. In this case, it's T1003, which is "Credential Dumping."



## Adding rules

We can follow either of the following methods to add custom rules:

* [GUI method](../../wazuh-manager/log-behaviour/adding-custom-wazuh-rules/gui-method.md)
* [CLI method](../../wazuh-manager/log-behaviour/adding-custom-wazuh-rules/cli-method.md)
