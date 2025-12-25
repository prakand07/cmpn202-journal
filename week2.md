**Week 2 — Security Planning and Testing Methodology**

Phase 2: Security Planning and Testing Methodology

Student Name: Prakand

Module: CMPN202

Week: 2

Phase Title: Security Planning and Testing Methodology

System: Ubuntu Server 24.04 LTS (VirtualBox)


**1. Introduction**

In Week 2, the focus was on designing a security baseline and a testing methodology for the Ubuntu Server environment installed in Week 1. The goal of this phase is to ensure that the server is protected against common threats while maintaining performance, reliability, and secure remote access.
This week covers:
  •	Performance testing and monitoring methodology
  •	Security configuration checklist
  •	Threat modelling with mitigation strategies

**2. Performance Testing & Monitoring Plan**

2.1 Objectives
The performance testing plan aims to:

  •	Monitor system resource usage
  •	Identify potential bottlenecks
  •	Ensure system stability under normal workloads
  •	Support future security and performance tuning

2.2 Monitoring Methodology

Performance monitoring is carried out using command-line tools native to Ubuntu Server.

**Component**

  CPU Usage
  Memory
  Disk Usage
  Network
  System Logs

**Tool**

  top, htop
  free -h
  df -h, du
  ip a, ss, ping
  journalctl


**Purpose**

  Monitor CPU load and running processes
  Check RAM and swap usage
  Monitor storage consumption
  Monitor connectivity and network interfaces
  Review system and security logs



2.3 Remote Monitoring Approach

  •	SSH is used for remote administration and monitoring.
  •	Secure access is restricted using firewall rules (UFW).
  •	Monitoring commands are executed remotely to simulate real-world server management.


2.4 Performance Testing Strategy

Testing is conducted during:

  •	Idle state (baseline performance)
  •	After enabling security services (UFW, SSH)
  •	During updates (apt update && apt upgrade)
  
Results are recorded to observe any performance degradation caused by security controls.


3. Security Configuration Checklist
The following checklist defines the minimum security baseline for the server.

3.1 SSH Hardening

  •	OpenSSH Server installed
  •	Password authentication enabled (for learning environment)
  •	Root login disabled
  •	Strong user password enforced
  •	SSH access restricted via firewall

3.2 Firewall Configuration (UFW)

  •	UFW enabled
  •	Default deny incoming traffic
  •	Allow SSH only

  
Commands used:

      sudo ufw enable
      sudo ufw default deny incoming
      sudo ufw default allow outgoing
      sudo ufw allow ssh
      sudo ufw status
<img width="814" height="415" alt="image" src="https://github.com/user-attachments/assets/93a7cc46-0380-49f3-8f28-85511fe0b826" />


 
3.3 User Privilege Management

   Non-root user created
   sudo used for administrative tasks
   Principle of least privilege applied

3.4 Automatic Updates

  Security updates enabled
  Regular patching supported

Command:

	sudo apt install unattended-upgrades

<img width="975" height="233" alt="image" src="https://github.com/user-attachments/assets/3fbd2032-a448-4031-bd33-6d32b833c8df" />

 
3.5 Network Security

     NAT networking used (VirtualBox)
     Private IP address assigned
     No direct public exposure
     
This reduces attack surface while allowing updates via Ubuntu repositories.


**4. Threat Model**

4.1 Identified Threats and Mitigations
Threat	Description	Mitigation
Brute-force SSH attacks	Unauthorized login attempts	SSH hardening, UFW, strong passwords
Unpatched vulnerabilities	Exploits of outdated software	Automatic updates, regular patching
Unauthorized access	Misuse of root privileges	Disable root login, use sudo


4.2 Threat Impact Analysis

  •	Likelihood: Medium (common attacks on exposed services)
  •	Impact: High (data compromise, service disruption)
  •	Risk Level: Reduced through layered security controls


5. Security Testing Approach
Security testing is conducted by:

    •	Verifying firewall rules
    •	Attempting login with incorrect credentials
    •	Reviewing authentication logs
   
Commands used:

    sudo ufw status
    journalctl -u ssh

<img width="594" height="183" alt="image" src="https://github.com/user-attachments/assets/faf02423-c61c-410d-a064-94a7fc91d191" />

 
**6. Reflection**

This week strengthened the security posture of the Ubuntu Server by introducing defensive controls, monitoring strategies, and threat awareness. The security baseline established in Week 2 provides a solid foundation for future configuration, automation, and advanced security tasks in later weeks.

**7. Conclusion**

Week 2 successfully delivered:

  •	A documented performance testing plan
  •	A comprehensive security configuration checklist
  •	A basic threat model with mitigation strategies
  
These outputs directly satisfy the Assessment Week 2 deliverables and prepare the system for advanced security implementation in Week 3 and beyond.
