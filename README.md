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


## Log Sources Used

- Windows Event Logs (SecurityEvent)  
- Linux Syslog Logs  
- Microsoft Sentinel Alerts  
- Azure Network Analytics

## Attack Maps (Before Hardening)

Before security controls, the environment received multiple attacks globally.

![Attack Map Before](https://github.com/vshuyong/Cloud-honeynet-security-architecture/blob/7f7e454bdd6cb438cfa334ff3df4bf4f8c35bb9c/linux_before.jpg)


## Attack Maps (After Hardening)

After hardening, attack activity dropped significantly.

![Attack Map After](images/map-after.png)



## Conclusion

This project demonstrates how proper cloud security configurations dramatically reduce real-world attack activity.

By implementing NSG restrictions, private endpoints, and firewall rules, the attack surface was minimized and malicious traffic was effectively reduced.


## Key Skills Demonstrated

- Microsoft Azure  
- Microsoft Sentinel (SIEM)  
- Log Analytics (KQL)  
- Network Security Groups (NSG)  
- Cloud Security Hardening  
