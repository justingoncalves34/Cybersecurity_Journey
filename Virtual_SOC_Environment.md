# Virtual SOC Environment 

---

[Back to Projects](Projects.md)

---

## Project Overview

In today's digital landscape, cybersecurity has become paramount for protecting sensitive information and maintaining organizational integrity. As cyber threats evolve in complexity and frequency, the need for effective monitoring and defense mechanisms has never been greater. In this project, I aim to establish a Virtual Security Operations Center (SOC) using Azure and Microsoft Sentinel, which will serve as a comprehensive platform for real-time security monitoring, incident response, and threat intelligence integration.

By creating a virtual environment to simulates real-world scenarios, I can gain hands-on experience exploring and implementing various cybersecurity practices and tools. The focus will be on deploying virtual machines (VMs), configuring them for security monitoring, and creating alert rules to detect and respond to potential threats. Through this initiative, I seek to enhance my technical skills and knowledge of security operations within cloud environments.

---

## Project Scope

The scope of this project is centered around the establishment of a Virtual Security Operations Center (SOC) within a cloud environment, utilizing Microsoft Azure and Microsoft Sentinel. The primary aim was to provide a comprehensive overview of how to monitor, detect, and respond to cybersecurity threats effectively.

Initially, I intended to deploy one Linux and one Windows server. Both servers were operational for a few days, but due to significantly higher activity observed on the Windows server, I decided to delete the Linux server and create a second Windows server. This adjustment allowed me to focus on monitoring real-world brute force attacks on both virtual machines.

I set up Microsoft Sentinel and Log Analytics to facilitate security monitoring, which involved creating multiple custom alert rules using Kusto Query Language (KQL) to detect potential threats and configuring data connectors through the content hub. The SOC was designed to actively monitor real-time attack attempts, particularly focusing on brute-force attacks directed at the deployed VMs.

Budget management was also crucial, as the project was conducted under the Azure Free Trial. I carefully monitored resource usage to avoid exceeding budget limits, utilizing the Cost Analysis dashboard to ensure the project remained within the confines of the available credits.

While the project aimed to achieve these objectives, it did not extend to extensive penetration testing or advanced incident response scenarios beyond what was achievable with the deployed VMs. By defining these parameters, I maintained focus throughout the project, ensuring that the objectives were met while effectively utilizing available resources.


---

## Objectives

1. **Establish a Virtual SOC**: To create a functioning Virtual Security Operations Center using Azure and Microsoft Sentinel, providing a platform for monitoring and analyzing security events in real-time.
2. **Implement Real-time Logging and Alerting**: To configure virtual machines to generate and send security logs to Microsoft Sentinel, and to create alert rules that identify potential security threats.
3. **Utilize Data Connectors**: To leverage the content hub in Microsoft Sentinel to set up various data connectors, enhancing the capability to detect and respond to emerging threats.
4. **Monitor Brute Force Attacks**: To observe and analyze the real-time brute force attack attempts received by the deployed virtual machines, evaluating the effectiveness of the alerting mechanisms.
5. **Manage Budget**: To effectively manage the project's budget by utilizing the Azure free trial credits and monitoring the Cost Analysis dashboard, ensuring that the project remains within budget constraints.
6. **Enhance Technical Skills**: To improve my understanding and technical proficiency in using cloud security tools and best practices for incident response and monitoring.

---

## Tools Used

To effectively implement the Virtual Security Operations Center (SOC) and ensure robust monitoring and management, I utilized a variety of tools and technologies throughout the project:

1. **Microsoft Azure**: The primary platform for deploying virtual machines and services, providing the necessary infrastructure for creating the virtual environment and managing resources efficiently.
2. **Microsoft Sentinel**: This cloud-native Security Information and Event Management (SIEM) solution was instrumental in monitoring security events, creating alerts, and facilitating incident response in real-time.
3. **Log Analytics**: Integrated with Microsoft Sentinel, Log Analytics enabled the collection and analysis of logs from my virtual machines, offering valuable insights into security events and system health.
4. **Virtual Machines**: I deployed multiple VMs, including Windows 11 Pro and Linux, to test various security configurations and actively monitor real-time attack attempts.
5. **Content Hub**: This feature allowed me to access and configure various data connectors within Microsoft Sentinel, enhancing the SOC's capability to detect and respond to emerging threats.
6. **Dashboards**: I utilized Azure dashboards to manage and monitor resource usage and security alerts, ensuring effective oversight of the project's operational state and maintaining the overall integrity of the SOC.
