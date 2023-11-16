# Overview of sentinel

## Security Information and Event Management with Microsoft Sentinel

Microsoft Sentinel is a powerful tool for collecting, analyzing, and responding to security data, while threat hunting is a proactive approach that complements automated security measures by actively searching for hidden threats. Together, they form a comprehensive strategy to enhance an organization's cybersecurity posture and protect against a wide range of threats.

### Key features of Microsoft Sentinel

- Log Collection: Microsoft Sentinel collects and centralizes log data from a wide range of sources, including servers, applications, devices, and cloud services.
- Threat Detection: It uses built-in and custom detection rules to identify suspicious activities and security threats in real time.
- Incident Investigation: Security analysts can use Microsoft Sentinel to investigate incidents, analyze logs, and visualize the scope of security threats.
- Automation: Sentinel offers automation capabilities to respond to common security incidents and orchestrate complex security workflows.
- Threat Intelligence: It integrates with threat intelligence feeds to enrich data and improve threat detection.
Integration: Microsoft Sentinel seamlessly integrates with other Microsoft security solutions and third-party tools.

### Key features of Threat Hunting

- Skilled Analysts: Threat hunting requires cybersecurity professionals with a deep understanding of attack techniques, tools, and indicators of compromise (IoCs).
- Data Analysis: Analysts analyze logs, network traffic, and other data sources to identify patterns or anomalies that may indicate security threats.
- Hypothesis-Driven: Threat hunting often involves forming hypotheses about potential threats and then investigating to validate or refute them.
- Continuous Process: Threat hunting is an ongoing and iterative process. It doesn't rely on specific rules but adapts to emerging threats.

### Labs Scenario
Contoso is a global organization with a complex IT infrastructure that includes a combination of on-premises data centers and cloud-based resources. They are looking to enhance their security posture by deploying Azure Sentinel, Microsoft's cloud-native security information and event management (SIEM) and security orchestration automation and response (SOAR) solution. Additionally, Contoso aims to onboard its cloud resources and servers to Azure Sentinel to gain better visibility and proactive threat detection and response capabilities.

In the pursuit of a robust cybersecurity strategy, Contoso recognizes the importance of proactive threat detection and continuous security monitoring. To achieve this, the organization has decided to implement a comprehensive log analytics and threat-hunting program.

By implementing a robust log analytics and threat-hunting program, Contoso aims to proactively identify and mitigate threats, reduce the risk of security breaches, and maintain a strong security posture in an ever-evolving threat landscape. This approach will enable Contoso to stay ahead of potential threats and protect its digital assets effectively.

### Azure services and related products

- Log Analytics Workspace
- Microsoft Sentinel
- Threat Hunting

### Lab Context

In this Hands-on Lab, you will learn how to use Microsoft Sentinel to perform threat hunting by running queries to investigate your hypothesis. You will get Hands-on experience with Azure resources and how to use Microsoft Sentinel to detect attacks.