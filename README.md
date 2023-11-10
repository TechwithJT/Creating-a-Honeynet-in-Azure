<h1>Azure Honeynet: Cyber threats in Real Time</h1>



<h2>Introduction</h2>
In this project, I simulate a small-scale honeynet that attracts real-world traffic from attackers around the world through Microsoft Azure. The goal throughout this project is to demonstrate best security practices, incident response tactics, and the effects of hardening your environment. We'll accomplish this by intentionally deploying virtual machines that have no safeguard from the public internet to attract attackers into our environment. Then after ingesting some log sources into Log Analytics Workspace, Microsoft Sentinel will come in to create attack maps, alerts, and incidents. In order to showcase metrics before and after hardening the environment based off the incidents generated from the 24 hour capture.
<br />


<h2>Azure Components Used</h2>

- <b>Azure Virtual Network (VNet)</b> 
- <b>Azure Network Security Group (NSG)</b>
- <b>Virtual Machines (2x Windows, 1x Linux)</b>
- <b>Log Analytics Workspace with Kusto Query Language (KQL) Queries</b>
- <b>Azure Key Vault</b>
- <b>Azure Storage Account</b>
- <b>Microsoft Sentinel</b>
- <b>Microsoft Defender for Cloud</b>

<h2>Architecture Before Hardening </h2>

- <b>In the "BEFORE" stage of the project, all resources were initially deployed with the hope that attraction would be gained from the public internet. The Virtual Machines had both their Network Security Groups (NSGs) and built-in firewalls wide open, allowing unrestricted access from any source. Additionally, all other resources, such as storage accounts and databases, were deployed with public endpoints visible to the internet, without utilizing any Private Endpoints for added security. These machines were then left to the public for 24 hours to generate the following attack maps mentioned earler.</b> (21H2)

<b>This attack map showcases the number of incidents generated by leaving the Network Security Group (NSG) open.</b> 


<p align="center">
Attack Map: <br/>
 
<img src="https://i.imgur.com/PN0ArE4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This attack map highlights the incidents for syslog authentication failures experienced by the Linux server.:  <br/>
<img src="https://i.imgur.com/N8rio0r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This attack map showcases RDP and SMB failures against the Window machine: <br/>
<img src="https://i.imgur.com/izaypM0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This attack map showcases failures against the MSSQL server.:  <br/>
<img src="https://i.imgur.com/OD1TipR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>After Hardening Measures and Security Controls</h2>
<b>In the "AFTER" stage, based off the incidents created from the "Before" 24 hour capture, I implemented hardening measures and security controls to improve the environment's security from attackers.
These improvements included:</b>

- <b>Network Security Groups (NSGs): I hardened the NSGs by only allowing my own public IP address to come thrugh otherwise all other traffic would be blocked by the new parameteres created.</b>
- <b>Built-in Firewalls: In my virtual machines I configured the built-in firewalls so that it would deny access from unauthorized users.</b>
- <b>Private Endpoints: For other Azure resources, I replaced the public endpoints with Private Endpoints. This ensured that access to sensitive resources, such as storage accounts and databases, was limited to only the virtual network.</b> 

<h2>Metrics Before Hardening / Security Controls</h2>

<b>The following table shows the metrics we measured in our insecure environment for 24 hours:</b> 

<b>Start Time 2023-11-10 09:15 AM</b> 

<b>Start Time 2023-11-11 09:30 AM:</b> 



Before Stats:  <br/>
<img src="https://i.imgur.com/s7AtaYj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>Metrics After Hardening / Security Controls</h2>
<b>The following table shows the metrics we measured in our secure environment for 24 hours:</b> 

<b>Start Time 2023-11-13 10:12 AM</b> 

<b>Start Time 2023-11-14 11:35 AM</b> 


After Hardening:  <br/>
<img src="https://i.imgur.com/wdAclZG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>Utilizing NIST 800.61r2 Computer Incident Handling Guide</h2>
For each simulated attack I practiced incident responses following NIST SP 800-61 r2.:  <br/>
<img src="https://i.imgur.com/9HHyJKe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<b>Each organization will have policies related to an incident response that should be followed. This event is just a walkthrough for possible actions to take in the detection of malware on a workstation.</b> 

<h2>Preperation</h2>

- <b>The Azure lab was set up to ingest all of the logs into Log Analytics Workspace, Sentinel and Defender were configured, and alert rules were put in place.</b>

<h2>Detection & Analysis</h2>

- <b>Malware has been detected on a workstation with the potential to compromise the confidentiality, integrity, or availability of the system and data.</b>
- <b>Assigned alert to an owner, set the severity to "High", and the status to "Active"</b>
- <b>Identified the primary user account of the system and all systems affected.</b>
- <b>A full scan of the system was conducted using up-to-date antivirus software to identify the malware.</b>
- <b>Verified the authenticity of the alert as a "True Positive".</b>
- <b>Sent notifications to appropriate personnel as required by the organization's communication policies.</b>

<h2>Containment, Eradication & Recovery</h2>
- <b>The infected system and any additional systems infected by the malware were quarantined.</b>
- <b>If the malware was unable to be removed or the system sustained damage, the system would have been shut down and disconnected from the network.</b>
- <b>Depending on organizational policies the affected systems could be restored known clean state, such as a system image or a clean installation of the operating system and applications. Or an up-to-date anti-virus solution could be used to clean the systems.</b>


<h2>Post-Incident Activity</h2>

- <b>In this simulated case, an employee had downloaded a game that contained malware.</b>
- <b>All information was gathered and analyzed to determine the root cause, extent of damage, and effectiveness of the response.</b>
- <b>Report disseminated to all stakeholders.</b>
- <b>Corrective actions are implemented to remediate the root cause.</b>
- <b>And a lessons-learned review of the incident was conducted.</b>


<h2>Conclusion</h2>

<b>In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. The significant reduction in security events and incidents following the implementation of security controls highlights their effectiveness in safeguarding the environment.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.</b>

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
