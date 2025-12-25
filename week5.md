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
 Screenshot evidence: aa-status output

2. Automatic Security Updates

Automatic updates reduce exposure to known vulnerabilities.

Installation

sudo apt update

 
sudo apt install unattended-upgrades –y

 
Enable Automatic Updates
sudo dpkg-reconfigure --priority=low unattended-upgrades
 
Verification
cat /etc/apt/apt.conf.d/20auto-upgrades
Configured to:
•	Automatically install security patches
•	Run daily


 Screenshot evidence: auto-updates configuration file

3. Intrusion Detection using Fail2Ban

Fail2Ban protects SSH from brute-force attacks.

Installation

sudo apt install fail2ban –y
 
 

Enable and Start

sudo systemctl enable fail2ban
sudo systemctl start fail2ban
Check Status
sudo fail2ban-client status
Configured Protection:
•	SSH service monitored
•	IP banned after repeated failures


 
Screenshot evidence: Fail2Ban status output

4. Security Baseline Verification Script

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
Make Executable & Run
chmod +x security-baseline.sh
./security-baseline.sh
📸 Screenshot evidence: script execution via SSH
________________________________________
5. Remote Monitoring Script
📄 File: monitor-server.sh (runs on workstation)
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
Make Executable & Run
chmod +x monitor-server.sh
./monitor-server.sh
📸 Screenshot evidence: monitoring output
________________________________________
6. Video Demonstration (Required)
Your video must show:
•	SSH login
•	Running security-baseline.sh
•	Running monitor-server.sh
•	Explanation of each security control
🎥 Length: 5–7 minutes
🎙️ Narration: Explain commands while running them
________________________________________
7. Summary
Week 5 implemented advanced security controls and monitoring infrastructure. AppArmor enforced access control, automatic updates ensured timely patching, and Fail2Ban provided intrusion detection. Custom scripts verified security baselines and enabled remote monitoring, strengthening system resilience and visibility.



