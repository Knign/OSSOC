# Aim of this project

## Automate Case Creation and Observables with Shuffle SOAR:&#x20;

Utilize Shuffle SOAR to automate the creation of security cases upon detection of high-priority events. Shuffle will trigger workflows that interact with TheHive. These workflows will create cases in TheHive and extract relevant indicators of compromise (IOCs) from the events (e.g., IP addresses, domains, URLs). Shuffle can then add these IOCs as observables to the corresponding case within TheHive.&#x20;

## Automate Threat Investigation Workflows:&#x20;

Integrate Cortex (by TheHive) with threat intelligence feeds and external analyzers. Upon case creation in TheHive, triggered by Shuffle workflows, Cortex can automatically run pre-configured investigation playbooks or any of the dedicated analyzers according to the detected incident. These playbooks can automate tasks like:&#x20;

* Enriching the case with threat intelligence data.&#x20;
* Assessing the risk associated with the observables.&#x20;
* Performing threat hunting on the network for related activity.&#x20;
* Collecting additional forensic evidence from endpoints.&#x20;
* Suggesting potential remediation actions.&#x20;

## Improve Analyst Efficiency:&#x20;

The automation of investigation tasks will free up analyst time for focusing on complex incidents requiring human expertise and judgment.&#x20;

## Reduction in time to investigate and respond to security incidents.&#x20;

## Decrease in the number of alerts requiring manual analysis by focusing on high-priority events.&#x20;

## Increased analyst productivity through automation of routine investigation tasks.&#x20;

## To gain relevant experience and understanding of the processes that are carried out in the SOC setup in the organizations and usage of tools for the same.&#x20;

## Reduce Costs:&#x20;

Utilize readily available open-source tools to establish a robust SOC solution without incurring significant licensing fees.
