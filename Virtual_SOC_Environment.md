# Virtual SOC Environment 

---

[Back to Projects](Projects.md)

---

## Project Overview

The Virtual Security Operations Center (SOC) project aimed to establish a comprehensive monitoring and incident response system in a cloud-based environment. Over the course of one month, I deployed multiple Windows 11 Pro virtual machines in Microsoft Azure, focusing on the real-time analysis of security events and the detection of potential threats. This project not only involved technical implementation but also practical applications of understanding cybersecurity threats in a virtual landscape.

During the project, I monitored over 7.6 million events and nearly 6,000 alerts, illustrating the complexity of data that modern SOCs manage. Implementing custom alert rules in Microsoft Sentinel with Kusto Query Language (KQL) allowed for tailored responses to specific threats, ensuring only significant incidents triggered alerts. This proactive approach enhanced efficiency in triage and response processes.

The project underscored the importance of maintaining vigilant monitoring practices and having incident response plans in place. The hands-on experience gained from configuring data connectors and analyzing real-time alerts has prepared me for the challenges within a Security Operations Center, ultimately equipping me to contribute meaningfully to the field and better protect critical assets in future roles.

---

## Table of Contents

1. [Project Scope](#project-scope)
2. [Objectives](#objectives)
3. [Tools Used](#tools-used)
4. [Implementation](#implementation)
5. [Results](#results)
6. [Conclusion](#conclusion)
7. [Personal Reflection](#personal-reflection)

---

## Project Scope

The scope of this project centers on establishing a Virtual Security Operations Center (SOC) within a cloud environment using Microsoft Azure and Microsoft Sentinel. The primary goal was to create a comprehensive system for monitoring, detecting, and responding to cybersecurity threats in real-time. Initially, I planned to deploy one Linux server alongside a Windows server; however, after observing significantly higher activity levels on the Windows server, I opted to delete the Linux server and create a second Windows server. This decision allowed me to concentrate my efforts on effectively monitoring real-world brute force attacks across both of the Windows virtual machines.

I implemented Microsoft Sentinel and Log Analytics for robust security monitoring, configuring multiple custom alert rules using Kusto Query Language (KQL) to identify potential threats. Additionally, I utilized the Content Hub to establish various data connectors that enhanced the SOC's capability to detect and respond to emerging threats. The SOC's design focused on actively monitoring real-time attack attempts, particularly brute-force attacks targeting the deployed VMs.

Effective budget management was a crucial aspect of the project, as it was conducted under the Azure Free Trial. I monitored resource usage closely to prevent exceeding budget limits, employing the Cost Analysis dashboard to ensure the project remained within the confines of available credits.

Overall, the project's scope was primarily dedicated to logging and monitoring, with an emphasis on developing strategies to detect and respond to cybersecurity threats while maximizing resource efficiency.

---

## Objectives

The primary objectives of this project are as follows:

1. **Establish a Virtual SOC**: To create a functioning Virtual Security Operations Center using Azure and Microsoft Sentinel, providing a platform for monitoring and analyzing security events in real-time.
2. **Implement Real-time Logging and Alerting**: To configure virtual machines to generate and send security logs to Microsoft Sentinel, and to create alert rules that identify potential security threats.
3. **Utilize Data Connectors**: To leverage the content hub in Microsoft Sentinel to set up various data connectors, enhancing the capability to detect and respond to emerging threats.
4. **Monitor Brute Force Attacks**: To observe and analyze the real-time brute force attack attempts received by the deployed virtual machines, evaluating the effectiveness of the alerting mechanisms.
5. **Manage Budget**: To effectively manage the project's budget by utilizing the Azure free trial credits and monitoring the Cost Analysis dashboard, ensuring that the project remains within budget constraints.
6. **Evaluate Security Posture**: To assess the overall security posture of the virtual environment through the analysis of logged events and alerts, identifying potential vulnerabilities and areas for improvement.
7. **Analyze Attack Patterns**: To conduct an analysis of the attack patterns observed during the monitoring phase, helping to inform future security strategies and defenses.
8. **Enhance Technical Skills**: To improve my understanding and technical proficiency in using cloud security tools and best practices for incident response and monitoring.

---

## Tools Used

To effectively implement the Virtual Security Operations Center (SOC) and ensure robust monitoring and management, I utilized a variety of tools and technologies throughout the project:

1. **Microsoft Azure**: The primary platform for deploying virtual machines and services, providing the necessary infrastructure for creating the virtual environment and managing resources efficiently.
2. **Microsoft Sentinel**: This cloud-native Security Information and Event Management (SIEM) solution was instrumental in monitoring security events, creating alerts, and facilitating incident response in real-time.
3. **Log Analytics**: Integrated with Microsoft Sentinel, Log Analytics enabled the collection and analysis of logs from my virtual machines, offering valuable insights into security events and system health.
4. **Virtual Machines**: I deployed multiple VMs, including Windows 11 Pro, to test various security configurations and actively monitor real-time attack attempts.
5. **Content Hub**: This feature allowed me to access and configure various data connectors within Microsoft Sentinel, enhancing the SOC's capability to detect and respond to emerging threats.
6. **Dashboards**: I utilized Azure dashboards to manage and monitor resource usage and security alerts, ensuring effective oversight of the project's operational state and maintaining the overall integrity of the SOC.
7. **Kusto Query Language (KQL)**: I employed KQL for writing custom queries to extract, analyze, and visualize log data, facilitating efficient monitoring and alerting in the SOC.

---

## Implementation

The implementation of the Virtual Security Operations Center (SOC) involved several key decisions that significantly influenced the setup and functionality of the monitoring system. Initially, I deployed both a Windows virtual machine and a Linux virtual machine; however, I ultimately decided to delete the Linux server in favor of deploying two Windows 11 Pro VMs. This change was prompted by the notably higher activity levels observed on the Windows server compared to the Linux server. To facilitate the project's objectives, I intentionally left the RDP port open to monitor any malicious behavior or brute force attacks aimed at accessing the RDP. As a result, I concentrated my efforts on these two Windows VMs, enabling a more comprehensive monitoring experience of real-world brute force attacks.

To facilitate effective security monitoring, I set up Microsoft Sentinel and Log Analytics. This involved creating custom alert rules using Kusto Query Language (KQL) to identify specific threats, such as brute force login attempts and unusual user behavior. Initially, I had configured the system to trigger incident creation for each brute force attempt; however, I soon realized that this approach resulted in a high volume of incidents—over 600—making it challenging to efficiently triage alerts. Consequently, I adjusted the settings so that only significant events, such as malware activity, account creation, RDP connections, and password change requests, would generate incidents in the future. This refinement enhanced the monitoring process, allowing for more effective triage of actual security threats.

I used the Content Hub in Microsoft Sentinel to integrate various data connectors. This allowed me to gather and analyze logs from different sources, providing a more holistic view of the security landscape. For instance, I configured Sentinel data connectors to collect logs from the Windows servers and connected Windows Security Events to monitor the activities on the Windows VMs.

The implementation of the SOC not only provided insights into attack patterns but also established a strong foundation for effective incident management. The knowledge gained from this hands-on experience has enhanced my understanding of security operations and equipped me with the skills necessary to thrive in a cybersecurity role.

### Configuration 

1. Below are the details showing the settings applied during the creation of the Windows Server 1 virtual machine.
![Windows Server 1 Configuration](images/virtual_soc/Windows_Server_1_Configuration.png)
*Configuration settings for the Windows Server 1 virtual machine.*

2. To facilitate remote access, the RDP port was intentionally left open, allowing for monitoring and management of the VM without restrictions.
![Allow RDP Port for Win Server](images/virtual_soc/Allow_RDP_Port_for_Win_Server.png)
*The configuration screen indicating that the RDP port is allowed for the Windows Server.*

3. If a hacker were to successfully gain access to the RDP, they would encounter this popular meme featuring a sad and defeated Toy Story character, providing a humorous but stark reminder of the potential consequences of unauthorized access.
![RDP Desktop](images/virtual_soc/RDP_Desktop.png)
*This image shows the RDP desktop of the Windows server.*

### Monitoring

I configured multiple custom rule alerts using KQL to enhance the monitoring capabilities of the SOC. The queries for these alerts were designed to capture various security events and behaviors, allowing me to respond quickly to potential threats. Below are some key custom alert rules that were implemented:

1. **Brute Force Attempt Rule Alert**  
```kql
SecurityEvent
| where EventID == 4625 // Failed logon attempt
| summarize Count = count() by Account, bin(TimeGenerated, 5m)
| where Count >= 5 // Threshold for alerting
```
*This query tracks repeated failed logon attempts, indicating a potential brute force attack.*

2. **Password Change Attempt Rule Alert**  
```kql
SecurityEvent
| where EventID == 4723 // Attempted password change
| project TimeGenerated, Account
```
*This rule generates alerts for any password change requests made on the system.*

3. **Systems Down Rule Alert**  
```kql
Heartbeat
| summarize LastHeartbeat = max(TimeGenerated) by Computer
| where LastHeartbeat < ago(5m)
```
*This alert monitors the heartbeat of the VMs to identify any unresponsive systems.*

4. **Unusual Account Behavior Rule Alert**  
```kql
SecurityEvent
| where EventID == 4624 // Successful logon
| summarize Count = count() by Account, bin(TimeGenerated, 1d)
| where Count < 5
```
*This query identifies unusual activities in user accounts that could indicate a potential security breach.*

The implementation of the SOC involved deploying two Windows 11 Pro virtual machines and configuring Microsoft Sentinel for comprehensive log analysis. Custom alert rules utilizing Kusto Query Language (KQL) enabled efficient monitoring of security incidents, allowing for quick identification of threats. This phase not only provided insights into attack patterns but also established a strong foundation for effective incident management.

---

## Results

### September 28th 24-Hour Analytics

The results from September 28th, just two days after the initiation of the Virtual Security Operations Center (SOC) project, reveal significant activity within the environment. As illustrated in the image below, there were a total of **620 incidents**, **629 alerts**, and **203.4K events** recorded during this 24-hour period. Initially, the high number of incidents was largely due to the setup where every brute force attempt was logged as an incident. Recognizing that this was inefficient for monitoring and triaging alerts, I adjusted the configuration to ensure that only significant events, such as malware activity, account creation, RDP connections, and password change requests, would generate incidents in the future.

![September 28th 24-Hour Logs](images/virtual_soc/sep_28th_24h_logs.png)  
*Overview of incidents, alerts, and events in Microsoft Sentinel on September 28th.*

### October 8th 24-Hour Analytics

The results from October 8th reflect the continuous activity within the Virtual Security Operations Center (SOC) project. As shown in the image below, there were **185 alerts**, **183.8K events**, and **0 incidents** recorded during this 24-hour period. This significant decrease in incidents indicates that the alerting system adjustments made previously were effective. By refining the conditions for generating incidents, I ensured that only critical events, such as malware activity, account creation, RDP connections, and password change requests, would result in incidents, allowing for more efficient monitoring and response.

![October 8th 24-Hour Logs](images/virtual_soc/Oct_8th_24h_Logs.png)  
*Overview of incidents, alerts, and events in Microsoft Sentinel on October 8th.*

### October 14th 24-Hour Analytics

The results from October 14th show **256 alerts**, **273K events**, and **0 incidents** recorded during this period, as indicated in the image below. This data reflects the ongoing activity and monitoring within the system.

![October 14th 24-Hour Logs](images/virtual_soc/Oct_14_24h_Logs.png)  
*Overview of incidents, alerts, and events in Microsoft Sentinel on October 14th.*

### October 22nd 24-Hour Analytics

The results from October 22nd show **300 alerts**, **235.9K events**, and **0 incidents** recorded during this period, as indicated in the image below. The data reflects ongoing monitoring activities within the system, with a notable number of alerts indicating various activities.

![October 22nd 24-Hour Logs](images/virtual_soc/Oct_22_24h_Logs.png)  
*Overview of incidents, alerts, and events in Microsoft Sentinel on October 22nd.*

### Overall Project Results

Throughout the duration of the project, the monitoring system captured a total of **7.6 million events**, resulting in **5.9K alerts** and **626 incidents**. These figures reflect the extensive activity monitored within the environment. Initially, the high number of incidents was primarily due to brute force attempts being logged as incidents, which created a cluttered monitoring experience. Recognizing this inefficiency, I adjusted the incident creation settings to ensure that only significant events—such as malware activity, account creations, RDP connections, and password change requests—would trigger incident alerts in the future. This change streamlined the monitoring process, allowing for more effective triage of actual security threats.

Upon analyzing the 24-hour logs, several patterns emerged. Notably, there were heightened peaks in alerts, particularly around **9 PM on October 8th**, suggesting potential increased attack activity during that time. Additionally, the majority of alerts were related to brute force attempts, emphasizing the ongoing threat of unauthorized access via weak passwords. 

Throughout the project, my primary focus was on reviewing the logs and alerts to ensure normal activities. I checked for legitimate logins and system maintenance tasks, confirming that any irregularities were promptly addressed. Significant alerts indicating potential unauthorized access were documented for further analysis, allowing for refinement of alert rules and enhancing monitoring accuracy.

![Full Project Logs](images/virtual_soc/Full_Project_Logs.png)  
*Overview of total events, alerts, and incidents logged during the project.*

Additionally, the project's budget was effectively managed, with a total expenditure of **$171.07** during the monitored period, demonstrating a commitment to cost-efficient operations while still achieving the project's objectives.

![SOC Cost Analysis](images/virtual_soc/SOC_Cost_Analysis.png)  
*Overview of the cost analysis dashboard showing project expenditure and resource allocation.*

---

## Conclusion

The implementation of the Virtual Security Operations Center (SOC) provided invaluable insights into the dynamics of monitoring and managing security within a virtual environment. Throughout the project, I deployed multiple Windows 11 Pro VMs and configured custom alert rules in Microsoft Sentinel, which allowed me to effectively monitor real-world brute force attacks and other security events. The results demonstrated the importance of adapting incident response strategies, as I adjusted alert triggers to enhance efficiency and focus on significant incidents.

This project highlighted the critical nature of continuous monitoring to protect vital assets from potential threats. The experience solidified my understanding of how SOCs operate, underscoring the necessity of having well-defined playbooks and incident response plans in place. By analyzing patterns in alert generation and recognizing peak activity times, I became more adept at navigating the complexities of cybersecurity operations.

Ultimately, this project has equipped me with practical experience in using cloud-native security tools and has deepened my understanding of the complexities involved in safeguarding digital environments. The knowledge gained throughout this project has laid a solid foundation for future endeavors in cybersecurity and reinforced my commitment to being proactive in identifying and responding to threats.


---

## Personal Reflection

Reflecting on this month-long project, I recognize the immense value of patience and persistence in the field of cybersecurity. The experience underscored the critical importance of continuous monitoring to safeguard vital assets and infrastructure from potential threats. I learned firsthand how essential it is to have well-defined playbooks and incident response plans in place to efficiently address and mitigate security incidents as they arise.

The project has significantly enhanced my technical skills and provided me with a deeper appreciation for the processes and protocols necessary in a Security Operations Center (SOC) environment. Engaging with real-time alerts and incidents sharpened my ability to analyze and respond to security events effectively. I now feel more equipped to navigate the complexities of cybersecurity operations, making me better prepared to contribute effectively in future roles.

Overall, this project not only solidified my commitment to proactive threat identification and response but also reinforced my passion for protecting critical digital infrastructures. The insights gained will undoubtedly shape my approach to future cybersecurity challenges and enhance my contributions to any team I join.

---

[Back to Projects](Projects.md)

---
