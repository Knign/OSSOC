# Mimikatz Workflow

## Download

You can download the Shuffle workflow for Mimikatz below:

{% embed url="https://github.com/O-S-S-O-C/shuffle-workflows/blob/main/Mimikatz.json" %}



## Configuration

Once downloaded, you can import this workflow into you Shuffle dashboard.&#x20;

After that is done, add in the following API keys for authentication:

1. TheHive API key
2. Cortex API key



## Workflow explanation

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### 1. Alert Extraction using Webhook

Wazuh alerts are obtained from the Wazuh server and posted to a webhook, facilitating efficient extraction and integration into the workflow for further processing and analysis.

### 2. Hash extraction

In this step, a regular expression is used to parse the Wazuh alerts, specifically targeting the hash value associated with a particular file. This extracted hash is then available for subsequent analysis or actions within the workflow.

### 3. Alert Creation in TheHive with Extracted Wazuh data

In this step, relevant information such as timestamp, IP address, alert title, and affected computer from the Wazuh alerts are extracted and utilized to create an alert within TheHive platform.&#x20;

This integration streamlines incident response by centralizing Wazuh alerts and associated data in TheHive, enabling security analysts to efficiently investigate, prioritize, and respond to potential security incidents. By consolidating pertinent information in one platform, this process enhances coordination and facilitates a more effective incident response workflow.&#x20;

### 4. Creation of Case using the Alert data

Using the information from the alert, a case is created in TheHive. This case can then be analyzed and tracked by a security team. Analysts can collaborate on cases from other teams as well.

### 5. Observable Creation in TheHive for Wazuh Alert Data

Following the creation of an alert in TheHive, this step involves generating an observable corresponding to the extracted Wazuh alert data. The significance lies in enriching the alert with additional contextual information, such as file hashes, URLs, or network indicators, enabling deeper analysis and correlation with other security events.&#x20;

This enhances the visibility and comprehensiveness of the incident response process within TheHive, empowering analysts to make well-informed decisions and take appropriate actions to mitigate security risks effectively.

### 6. Extraction of Observable ID from TheHive Alert

This step involves extracting the observable ID associated with the created observable in TheHive alert. The observable ID serves as a unique identifier for the specific observable within TheHive platform. Its significance lies in facilitating further reference and correlation with other observables, aiding in the comprehensive analysis of security incidents. This extracted ID enables seamless integration with other security tools or processes, enhancing overall incident response capabilities and ensuring a coordinated approach to addressing security threats.

### 7. Cortex Integration: Comprehensive VirusTotal Analysis

This phase involves forwarding TheHive observable to Cortex, leveraging various analyzers to enable multiple layers of analysis, including VirusTotal scanning. This comprehensive approach enhances threat intelligence, swiftly identifying risks associated with the observable, and empowering proactive incident response, thereby strengthening cybersecurity defenses.
