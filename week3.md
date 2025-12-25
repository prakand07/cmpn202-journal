**CMPN202 – Week 3**

Phase 3: Application Selection for Performance Testing

Student Name: Prakand

Module: CMPN202

Week: 3

Focus: Application Selection & Performance Evaluation Planning


**1. Introduction**
The objective of Week 3 is to select appropriate applications that represent different workload types in order to evaluate the performance of the Ubuntu Server 24.04 LTS virtual machine. These applications are chosen to simulate real-world server workloads, including CPU-intensive, memory-intensive, I/O-intensive, network-intensive, and server-oriented services.

All applications will be installed and tested on the Ubuntu Server VM running inside Oracle VirtualBox, accessed remotely via SSH.

**2. Application Selection Matrix**

**Workload Type**
   CPU-intensive
   Memory-intensive
   I/O-intensive
   Network-intensive
   Server Application

  
**Application**
    stress-ng
    stress-ng (vm test)
    fio
    iperf3
    OpenSSH Server

3. Installation Documentation (SSH-based)
All installations are performed after logging into the server using SSH:
ssh prakand@10.0.2.15
 
3.1 Update System Packages
sudo apt update && sudo apt upgrade –y
 

3.2 Install stress-ng (CPU & Memory Testing)
sudo apt install stress-ng –y
  
3.3 Install fio (Disk I/O Testing)
sudo apt install fio –y
 
3.4 Install iperf3 (Network Testing)
sudo apt install iperf3 –y
 
3.5 Install OpenSSH Server (Server Application)
sudo apt install openssh-server -y
sudo systemctl enable ssh
sudo systemctl start ssh
 
4. Expected Resource Profiles
Application	CPU Usage	Memory Usage	Disk I/O	Network
stress-ng (CPU)	Very High	Low	Minimal	None
stress-ng (Memory)	Medium	Very High	Low	None
fio	Medium	Low	Very High	None
iperf3	Low	Low	Low	Very High
OpenSSH Server	Low	Low	Minimal	Moderate

5. Monitoring Strategy
The following tools and commands will be used to monitor system performance during testing:
CPU & Memory Monitoring
htop

 
free –h
 
Disk Performance
df -h
iostat
 
Network Performance
ip addr
ss –tuln
 
Real-time Logs
journalctl –xe
 

6. Justification of Application Choices
•	stress-ng allows controlled and repeatable CPU and memory stress testing.
•	fio provides detailed disk performance metrics suitable for server evaluation.
•	iperf3 accurately measures network throughput in virtualized environments.
•	OpenSSH Server reflects a realistic, always-on server workload.
These applications together provide broad performance coverage, ensuring reliable evaluation of system capabilities under different conditions.

7. Conclusion
Week 3 successfully defines a structured and justified set of applications for performance testing. The selected tools represent real-world server workloads and prepare the system for advanced configuration, security testing, and performance evaluation in subsequent weeks.
 

