**Week 7 – Security Audit and System Evaluation
**


**7.1 Objective
**

The objective of Week 7 was to conduct a full security audit of the server, validate security controls implemented in previous weeks, and assess remaining risks.


**7.2 Security Audit Tools Used
**

**Task**

	System Hardening Audit
	
	Network Security Scan
	
	SSH Verification
	
	Service Inventory


Tool

	Lynis
	
	nmap
	
	Manual inspection + testing
	
	systemctl list-units



**7.3 Lynis Security Scan
**

A Lynis audit was performed using:

	sudo lynis audit system

Results

•	Security score improved after Week 5 controls

•	Warnings reduced after firewall and AppArmor configuration

•	Recommendations documented for future improvements


**7.4 Network Security Assessment**

Using nmap, the following was verified:

•	Only SSH port (22) open

•	Firewall rules enforced correctly

•	No unnecessary services exposed


nmap -sS <server-ip>


**7.5 SSH Security Verification**

Verified:

•	Key-based authentication enabled

•	Password authentication disabled

•	Root login disabled

•	Access restricted to authorised user


**7.6 Service Audit and Justification**


**Service**

	SSH
	
	UFW
	
	Fail2Ban
	
	Unused services


**Status**

	Enabled
	
	Enabled
	
	Enabled
	
	Disabled


**Justification**

	Remote administration
	
	Firewall protection
	
	Intrusion prevention
	
	Reduced attack surface


**7.7 Risk Assessment**

**Risk**

Brute-force attacks
Unauthorised access
Network exposure
Misconfiguration



Mitigation
Fail2Ban
SSH keys
Firewall rules
Audit scripts


Residual risk is considered low, suitable for a small-scale secure server deployment.




**7.8 Overall System Evaluation
**

The system demonstrates: 

	•	Stable performance under load
	
	•	Effective security controls

	•	Minimal exposed attack surface
	
	•	Compliance with assessment requirements

The server is well-configured for secure remote administration and future scalability.
