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

**Category**

      Benchmarking Tool
      Benchmarking Tool
      Disk Benchmark Tool
      Network Testing Tool
      Remote Access Service


**Reason for Selection**

         Generates sustained CPU load to test processor performance
         Allocates large memory blocks to evaluate RAM usage and swapping
         Measures disk read/write throughput and latency
         Tests network bandwidth and packet transfer performance
         Represents real production server workload



**3. Installation Documentation (SSH-based)**

All installations are performed after logging into the server using SSH:

      ssh prakand@10.0.2.15
<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/e5bc07c0-01e7-4f9c-a725-d3c900c44efc" />

 
**3.1 Update System Packages**

      sudo apt update && sudo apt upgrade –y
<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/8b57d8c0-56f6-4d31-a4e8-cf1a078a40b3" />

 

**3.2 Install stress-ng (CPU & Memory Testing)**

      sudo apt install stress-ng –y
<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/8ef7dc59-77cd-42c4-93df-6f0f697deba3" />

  
**3.3 Install fio (Disk I/O Testing)**

      sudo apt install fio –y
<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/8a66ddad-a670-4a22-a6c1-ab64b8eda806" />

 
**3.4 Install iperf3 (Network Testing)**

      sudo apt install iperf3 –y
<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/4c4d7e72-6d8a-477f-9460-3be660fa513a" />

 
**3.5 Install OpenSSH Server (Server Application)**

      sudo apt install openssh-server -y
      sudo systemctl enable ssh
      sudo systemctl start ssh

<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/31438d26-1c06-4de6-a3f5-5ba14ceb02af" />

 
**4. Expected Resource Profiles**

**Application**

      stress-ng (CPU)
      stress-ng (Memory)
      fio
      iperf3
      OpenSSH Server

**CPU Usage**

      Very High
      Medium
      Medium
      Low
      Low

   
**Memory Usage**

      Low
      Very High
      Low
      Low
      Low


**Disk I/O**

      Minimal
      Low
      Very High
      Low
      Minimal


**Network**

      None
      None
      None
      Very High
      Moderate


**5. Monitoring Strategy**

The following tools and commands will be used to monitor system performance during testing:

CPU & Memory Monitoring

      htop
<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/b98e6aa1-ac6e-4369-ad50-b570b5c6f823" />


 
      free –h
<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/54589449-23b2-438c-9cd9-3093176fb97b" />

 
**Disk Performance**

      df -h
      iostat

<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/e217eb30-3c24-4b26-9305-61dacafd3c5c" />

 
**Network Performance**

      ip addr
      ss –tuln

<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/7cac789c-2dc9-46e4-8f47-9cdeef2ff7ab" />

 
**Real-time Logs**

      journalctl –xe
      
<img width="975" height="856" alt="image" src="https://github.com/user-attachments/assets/d8fc5d5e-895c-4010-aac3-5c2a6cf6b03a" />


      
 

**6. Justification of Application Choices**

      •	stress-ng allows controlled and repeatable CPU and memory stress testing.
      
      •	fio provides detailed disk performance metrics suitable for server evaluation.
      
            •	iperf3 accurately measures network throughput in virtualized environments.
            
      •	OpenSSH Server reflects a realistic, always-on server workload.
      

These applications together provide broad performance coverage, ensuring reliable evaluation of system capabilities under different conditions.

**7. Conclusion**

   Week 3 successfully defines a structured and justified set of applications for performance testing. The selected tools represent real-world server workloads and prepare the system for advanced configuration, security testing, and performance evaluation in subsequent weeks.
    

