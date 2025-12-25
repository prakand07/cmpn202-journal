**WEEK 5 — Advanced Security and Monitoring Infrastructure**

Phase 5: Advanced Security and Monitoring
Student Name: Prakand

Module: CMPN202

Server OS: Ubuntu Server 24.04 LTS

Access Method: SSH from workstation


**1. Access Control Implementation (AppArmor)**

Ubuntu uses AppArmor by default. It provides mandatory access control by enforcing application profiles.


**Check AppArmor Status**

    sudo aa-status

Result:

•	AppArmor enabled

•	Enforcing mode active

•	Profiles loaded for system services


Why AppArmor?

•	Lightweight and integrated with Ubuntu

•	Application-level security

•	Prevents privilege escalation and misuse

<img width="975" height="935" alt="image" src="https://github.com/user-attachments/assets/f440ba67-fdab-4bc8-b3ec-4b52a8bbf8b9" />
Screenshot evidence: aa-status output



**2. Automatic Security Updates**

Automatic updates reduce exposure to known vulnerabilities.

**Installation**

    sudo apt update
<img width="975" height="216" alt="image" src="https://github.com/user-attachments/assets/8df07d00-1cee-4098-8c75-7135f675ee78" />

 
    sudo apt install unattended-upgrades –y
<img width="975" height="152" alt="image" src="https://github.com/user-attachments/assets/da424e09-3abf-4955-ac3d-583a3db5a660" />


 
**Enable Automatic Updates**

    sudo dpkg-reconfigure --priority=low unattended-upgrades
<img width="975" height="935" alt="image" src="https://github.com/user-attachments/assets/a36100f6-622d-4153-9109-295b3ff2f7ff" />



 
**Verification**

    cat /etc/apt/apt.conf.d/20auto-upgrades


**Configured to:**

•	Automatically install security patches

•	Run daily

<img width="975" height="92" alt="image" src="https://github.com/user-attachments/assets/177aab1b-c92f-4d3c-82c1-65ea6c564f7a" />
Screenshot evidence: auto-updates configuration file



**3. Intrusion Detection using Fail2Ban**

Fail2Ban protects SSH from brute-force attacks.

**Installation**

    sudo apt install fail2ban –y
 <img width="975" height="935" alt="image" src="https://github.com/user-attachments/assets/c683ca79-49c1-40e9-acd4-52637515c8a1" />
<img width="975" height="935" alt="image" src="https://github.com/user-attachments/assets/411f1307-f983-454d-bffe-c21f41ff98fd" />

 
**
Enable and Start
**

sudo systemctl enable fail2ban

sudo systemctl start fail2ban

**Check Status**

sudo fail2ban-client status
Configured Protection:

  •	SSH service monitored
  
  •	IP banned after repeated failures



<img width="975" height="191" alt="image" src="https://github.com/user-attachments/assets/9698c9bb-7239-424b-963d-37fba0031de2" />
Screenshot evidence: Fail2Ban status output



**4. Security Baseline Verification Script**

File: security-baseline.sh (runs on server)

    #!/bin/bash
    # security-baseline.sh
    # Verifies security configurations from Weeks 4 and 5
    
    echo "=== Security Baseline Verification ==="
    
    echo "[1] Checking SSH service..."
    systemctl is-active ssh && echo "SSH is running"
    
    echo "[2] Checking firewall status..."
    sudo ufw status verbose
    
    echo "[3] Checking Fail2Ban status..."
    sudo systemctl is-active fail2ban && echo "Fail2Ban is active"
    
    echo "[4] Checking automatic updates..."
    cat /etc/apt/apt.conf.d/20auto-upgrades
    
    echo "[5] Checking AppArmor status..."
    sudo aa-status
    
    echo "=== Security check completed ==="






**5. Remote Monitoring Script**

File: monitor-server.sh (runs on workstation)


    #!/bin/bash
    # monitor-server.sh
    # Collects performance metrics from remote server via SSH
    
    SERVER_USER=prakand
    SERVER_IP=10.0.2.15
    
    echo "=== Remote Server Monitoring ==="
    
    ssh $SERVER_USER@$SERVER_IP << EOF
    echo "Hostname:"
    hostname
    
    echo "Uptime:"
    uptime
    
    echo "CPU Load:"
    top -bn1 | head -5
    
    echo "Memory Usage:"
    free -h
    
    echo "Disk Usage:"
    df -h
    EOF
    
    echo "=== Monitoring completed ==="


    
**6. Video Demonstration (Required)**

Your video must show:

•	SSH login

•	Running security-baseline.sh

•	Running monitor-server.sh

•	Explanation of each security control

🎥 Length: 5–7 minutes

🎙️ Narration: Explain commands while running them



**7. Summary**

Week 5 implemented advanced security controls and monitoring infrastructure. AppArmor enforced access control, automatic updates ensured timely patching, and Fail2Ban provided intrusion detection. Custom scripts verified security baselines and enabled remote monitoring, strengthening system resilience and visibility.



