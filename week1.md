1. Introduction
The purpose of Week 1 is to plan the system architecture and select an appropriate server operating system for a secure Linux server environment. This phase focuses on understanding the host–guest architecture, virtualization approach, network design, and justifying the choice of Linux distribution.
The environment is implemented using Oracle VirtualBox on a Windows workstation, hosting an Ubuntu Server 24.04 LTS virtual machine.
2. System Architecture Overview
The system consists of:
    •	A Windows 10/11 host workstation
    •	Oracle VirtualBox as the virtualization platform
    •	An Ubuntu Server 24.04 LTS virtual machine
    •	NAT networking for internet access and package updates
The host provides hardware resources (CPU, RAM, disk), while the Ubuntu Server VM is isolated and used for secure server configuration and testing.


3. System Architecture Diagram
The following diagram illustrates the relationship between the workstation, VirtualBox, Ubuntu Server VM, and the network.


 
architecture-diagram.png

4. Distribution Selection and Justification
Selected Distribution: Ubuntu Server 24.04 LTS
Reasons for selection:
•	Long Term Support (LTS) with updates until 2029
•	Stable and widely used in enterprise environments
•	Strong security update support
•	Excellent documentation and community support
•	Native compatibility with OpenSSH, UFW, and monitoring tools

Alternative Distributions Considered
Distribution	Reason Not Selected
CentOS Stream	Rolling-release model, less stable
Debian Server	Slower update cycle
Rocky Linux	More enterprise-focused, higher complexity
Arch Linux	Not suitable for production server environments

Ubuntu Server provides the best balance between security, stability, and ease of management.

5. Workstation Configuration Decision
The workstation is configured as follows:
•	Operating System: Windows 10/11
•	Virtualization Software: Oracle VirtualBox
•	Purpose: Host and manage the Ubuntu Server VM
Justification:
•	VirtualBox is free and widely supported
•	Supports snapshots and network isolation
•	Allows safe experimentation without affecting the host system

6. Network Configuration (Initial)
•	Network Mode: NAT
•	Interface Name: enp0s3
•	Example IP Address: 10.0.2.15
•	Purpose:
o	Internet access for package updates
o	Secure default networking
o	No direct external exposure
NAT was selected for Week 1 to simplify setup and reduce security risks during early stages.

7. System Specification (CLI Evidence)
The following Linux commands are used to document system information:
uname -a
free -h
df -h
ip addr
lsb_release -a
These commands provide kernel details, memory usage, disk allocation, network interfaces, and distribution information.
 <img width="975" height="866" alt="image" src="https://github.com/user-attachments/assets/a05f8135-6556-4a31-839e-7b105d051ab7" />


8. Summary
Week 1 successfully establishes the foundation for the secure server project. The system architecture has been planned, the operating system selected and justified, and the virtualization and networking environment prepared for future security configuration.
Subsequent weeks will build on this foundation by implementing security controls, firewall rules, monitoring tools, and performance evaluation.
