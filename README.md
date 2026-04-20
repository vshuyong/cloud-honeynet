# Cloud-honeynet-security-architecture

![image alt](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/dc34a0875b45f9cfff9fac7c064d913876aefdbb/Architecture_overview.png)

Azure cloud honeynet project using Microsoft Sentinel to detect, analyze, and reduce real-world attacks through security hardening.
## Introduction
In this project, I built a mini honeynet in Microsoft Azure and integrated multiple log sources into a Log Analytics Workspace. Microsoft Sentinel was then used to analyze logs, generate alerts, and visualize attacks.

I first observed activity in an insecure environment, then applied security hardening techniques and compared the results.


## Architecture Before Hardening

In the initial setup, all resources were exposed to the public internet.

- Network Security Groups (NSGs) were wide open  
- Virtual Machines allowed inbound traffic from anywhere  
- No Private Endpoints were used  

This made the environment highly vulnerable to external attacks.

![Before Hardening](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/b68861ea3bbeac7d1d95a9fd9951abe938866454/Architecture_Before.png)

## Architecture After Hardening

After applying security controls:

- NSGs were restricted (only my IP allowed)  
- Private Endpoints were implemented  
- Firewalls were enforced  

This significantly reduced attack surface.

![After Hardening](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/ec416d99b380f1e57e5d8562473d02781eefd02c/Architecture_After.png)

## Threat Investigation & Analysis

During this project, I used Microsoft Sentinel to investigate security alerts and incidents generated from the honeynet environment. This allowed me to analyze real attack activity targeting the exposed resources before hardening.

### Incident Overview

I reviewed multiple incidents, including failed and successful login attempts as well as brute-force attacks against both Windows and Linux virtual machines.

![Incident Overview](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/2e1c323ef1c4412d25a3f9a3f001bdcfa3da3438/Incident_Overview.jpg)


### Incident Analysis

By exploring individual incidents, I was able to examine alert details, timelines, and affected assets. This helped me understand how attackers were attempting to gain unauthorized access and how the system responded to these threats.

![Incident Details](images/incident-details.png)

---

### Attacker IP Investigation

Using Microsoft Sentinel’s investigation features, I analyzed attacker IP addresses and gathered detailed threat intelligence. This included:

- Geographic location (country, city)  
- Internet Service Provider (ISP)  
- ASN (Autonomous System Number)  
- Latitude and Longitude  

This information provided visibility into where the attacks were originating from and helped identify patterns in malicious activity.

![IP Investigation](images/ip-investigation.png)

---

### Findings

- Multiple brute-force attempts were detected from external IP addresses  
- Attackers originated from different global locations  
- Repeated login attempts targeted publicly exposed virtual machines  
- High-severity alerts were generated for credential access attempts  

---

### Outcome

The investigation confirmed that the environment was actively targeted before hardening. After implementing security controls and monitoring the environment for 24 hours, no new attack activity was observed in the logs or maps. This demonstrates that the applied security measures were effective in preventing further unauthorized access.


## Log Sources Used

- Windows Event Logs (SecurityEvent)  
- Linux Syslog Logs  
- Microsoft Sentinel Alerts  
- Azure Network Analytics

## Attack Maps (Before Hardening)

Before security controls, the environment received multiple attacks globally.

![Attack Map Before](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/7f7e454bdd6cb438cfa334ff3df4bf4f8c35bb9c/linux_before.jpg)

![Attack Map Before](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/77a943074b8b14fa0d468ff9f93f0218c5aa1e47/linux_before2.jpg)

![Attack Map Before](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/79824ae4df17114107c0c7ff3bf7c202f28ae3d9/mssql_before.jpg)

![Attack Map Before](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/12f7de76f4c02f453f61ae8a2bdf23910f2240f9/windows_before.jpg)

## Attack Maps (After Hardening)

After hardening, attack activity dropped significantly. After 24 hours of applying security controls, I queried the attack maps in Microsoft Sentinel. No results were returned, indicating that no malicious inbound activity was detected during that period. This confirms that the implemented hardening measures—such as restricting NSGs, removing public exposure, and enforcing private access—were effective in preventing external attacks.

![Attack Map After](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/b5dde6ead6611d6f131a3c6b3cedcc1836fc7546/Attack_Map_After.jpg)


## Conclusion

This project demonstrates how proper cloud security configurations dramatically reduce real-world attack activity.

By implementing NSG restrictions, private endpoints, and firewall rules, the attack surface was minimized and malicious traffic was effectively reduced.


## Key Skills Demonstrated

- Microsoft Azure  
- Microsoft Sentinel (SIEM)  
- Log Analytics (KQL)  
- Network Security Groups (NSG)  
- Cloud Security Hardening  
