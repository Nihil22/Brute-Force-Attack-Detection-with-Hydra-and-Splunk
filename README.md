# Brute-Force-Attack-Detection-with-Hydra-and-Splunk
Cybersecurity attack/detection Homelab using Splunk, Hydra, SSH, and VM's to simulte real world attack and threat detection

PROJECT:
---------------------------------------------------------------------------------------------------------------------------------
This lab is used to simulate an real cyber attack and log detection. Utilizing Hydra, SSH, & Splunk I will use Virtual machines to simulate attack and victium machines. The attack machine will be a kali linux virtual machine with hydra to brute force the Ubuntu(victim) machine. 

SETUP:
---------------------------------------------------------------------------------------------------------------------------------
My perosnal setup was a two VMs deployed by virtual box one containg Kali linux to be used as the attack machine which will leverage the rockyou.txt password list and one using ubuntu as the victum machine. In order to allow my victium machine to be vulnerable I turned off the default ufw on the machine and opened port 22 on the machine. Both VMs were already deployed and setup before lab.
Target Machine setup:

https://github.com/Nihil22/Brute-Force-Attack-Detection-with-Hydra-and-Splunk/blob/main/Screenshot%202025-10-26%20192340.png?raw=true

Enumeration:
---------------------------------------------------------------------------------------------------------------------------------
To enumarte the network i conducted a Nmap scan on the attack machine to scan the local network for active host and open ssh port (22)

IMG:

Identified the Ubuntu victim with open port 22

IMG:

SSH Brute Force Attack using Hydra:
---------------------------------------------------------------------------------------------------------------------------------
used hydra to attempt brute force login against the target

Img:

Hydra trys passwords from the rockyou.txt list to gain access to victim SSH account

Monitoring Vicim logs:
---------------------------------------------------------------------------------------------------------------------------------
analyzed linux authentication logs to detect brute force

img:

Looked for fail login attempts which ID brute force

SIEM Ingestion
---------------------------------------------------------------------------------------------------------------------------------
Ensured the logs were formatted and readable, then install and configured Splunk Universal Forwarder on Ubuntu VM:

Img:

Log Ingestion
---------------------------------------------------------------------------------------------------------------------------------
verified that the victim machine logs were indexed to splunk. Searched for login faliures to confirm

Img:

DETECTION and Alerting
---------------------------------------------------------------------------------------------------------------------------------
created splunk alerts for Brute force detection, filtered for repeated login.

Img:

Tools Used
---------------------------------------------------------------------------------------------------------------------------------
Kali Linux: Attacker VM
Ubuntu Linux: Target VM
Nmap: Network scanning
Hydra: SSH brute-force tool
OpenSSH: SSH service on victim
rockyou.txt: Password list for brute-force
Splunk Universal Forwarder & Splunk Enterprise: Log collection, ingestion, and SIEM analysis

Summary:
---------------------------------------------------------------------------------------------------------------------------------
This lab successfully demonstrates how an SSH brute-force attack occurs and how system logs can detect it. By forwarding logs to Splunk, alerts can be generated to identify malicious activity in real-time. The lab highlights the importance of monitoring authentication logs and integrating SIEM tools for proactive threat detection.
