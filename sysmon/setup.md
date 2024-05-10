# Installation

## Download and Setup

First, we need to download the latest Sysmon version from the following link:

{% embed url="https://download.sysinternals.com/files/Sysmon.zip" %}

Next, we have to download the Configuration file for Sysmon to run properly.&#x20;

{% embed url="https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml" %}

Make sure that the configuration file is in the same directory as the extracted Sysmon files.

```
       Extracted Sysmon directory
            |
   +--------+---------+
   |                  |
sysmonconfig.xml   other files
```



## Installation

Open PowerShell with administrator privileges and change directory to the one in which Sysmon is downloaded.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\Users\{User}\Downloads\Sysmon>
```
{% endcode %}

Then we have to execute the `Sysmon64.exe` file and install the `sysmonconfig.xml` configuration file.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\Users\{User}\Downloads\Sysmon> .\Sysmon64.exe -i sysmonconfig.xml
```
{% endcode %}

We can then verify that Sysmon is running using the `Get-Process` cmdlet.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\Users\{User}\Downloads\Sysmon> Get-Process Sysmon64
```
{% endcode %}
