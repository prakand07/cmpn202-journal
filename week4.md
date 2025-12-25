
 
**CMPN202 – Week 4 Journal**

Phase 4: Initial System Configuration & Security Implementation

Student Name: Prakand

Module: CMPN202

Week: 4

Server OS: Ubuntu Server 24.04 LTS

Virtualisation: Oracle VirtualBox

**4.1 Objective**

The objective of Week 4 was to deploy the Ubuntu Server and implement foundational security controls. All administrative actions were performed remotely via SSH from the workstation, in line with the assessment constraints.

Key security goals:

  •	Secure remote access using SSH key-based authentication
  •	Restrict network access using a firewall
  •	Implement least-privilege user management
  •	Verify secure remote administration



**4.2 SSH Key-Based Authentication Configuration**

**Step 1: Generate SSH Key on Workstation**

    ssh-keygen -t ed25519 -C "prakand@cmpn202"
  
Keys generated:

    •	Private key: ~/.ssh/id_ed25519
    •	Public key: ~/.ssh/id_ed25519.pub

<img width="975" height="935" alt="image" src="https://github.com/user-attachments/assets/2ad628fa-1e6a-4176-8967-d8ea2757c6ed" />


     
**Step 2: Verify SSH Login**

    ssh prakand@10.0.2.15
<img width="975" height="935" alt="image" src="https://github.com/user-attachments/assets/a2805715-4608-4f17-81fc-d5b3d253e146" />

Successful passwordless SSH login confirmed.

**4.3 SSH Hardening**

Configuration File

    sudo nano /etc/ssh/sshd_config
<img width="975" height="935" alt="image" src="https://github.com/user-attachments/assets/76edab8d-fadf-442f-a3c8-e72df8dd3200" />

Apply Changes

    sudo systemctl restart ssh
<img width="975" height="935" alt="image" src="https://github.com/user-attachments/assets/0eeeabae-9fae-44d8-aa63-23bc60e2f9ec" />

 
**4.4 Firewall Configuration (UFW)**

Install and Enable UFW

    sudo apt update
<img width="975" height="209" alt="image" src="https://github.com/user-attachments/assets/f486fa89-e80c-4fdd-b266-428922f0e293" />


 
    sudo apt install ufw –y
<img width="975" height="170" alt="image" src="https://github.com/user-attachments/assets/3e4f49a8-5f94-46d8-9c92-b6eb6e45fe41" />

 
    sudo ufw enable
<img width="975" height="74" alt="image" src="https://github.com/user-attachments/assets/7682f7b8-0f21-498a-a8a1-b9aeeb5a3690" />


 


**Default Firewall Policy**

    sudo ufw default deny incoming
<img width="975" height="137" alt="image" src="https://github.com/user-attachments/assets/7a6df0c3-8cc7-49c7-a2ae-5bee9a345fd6" />

 
    sudo ufw default allow outgoing
<img width="975" height="703" alt="image" src="https://github.com/user-attachments/assets/d29635a1-fa38-4db6-a0e1-673878b6ec29" />

 

**Firewall Status**

    sudo ufw status verbose
<img width="975" height="261" alt="image" src="https://github.com/user-attachments/assets/3f6e1e3e-0615-4537-818b-94086874babc" />

 
**Result:**
Status: active

    22/tcp ALLOW IN from 10.0.2.2

SSH access restricted to a single trusted workstation.


**4.5 User and Privilege Management**

Verify Non-Root Admin User


    Whoami
<img width="975" height="74" alt="image" src="https://github.com/user-attachments/assets/99f01aa3-fcb2-493f-b574-cb99946cc45f" />

Output:
prakand

**Confirm Sudo Access**

sudo whoami
Output: 
<img width="975" height="66" alt="image" src="https://github.com/user-attachments/assets/695315dc-e53e-47c8-b34e-224ace43f366" />

root

**4.6 Remote Administration Evidence**

**Example Remote Commands Executed via SSH**

    uptime
    df -h
    free -m
    sudo apt update
<img width="975" height="935" alt="image" src="https://github.com/user-attachments/assets/3a491906-166d-4bc3-af9a-99bb766da43f" />
All commands executed successfully over SSH from the workstation.

**4.7 Configuration Files Evidence**

File

  /etc/ssh/sshd_config
  /etc/ufw/user.rules
  ~/.ssh/authorized_keys


Purpose

  SSH hardening
  Firewall rules
  SSH public keys

**4.8 Security Outcomes**

Control

SSH Key Authentication
Password Authentication
Root SSH Login
Firewall Enabled
Restricted SSH Access
Remote Admin via SSH


Status

✅ Implemented
❌ Disabled
❌ Disabled
✅ Active
✅ Workstation only
✅ Verified

**4.9 Reflection**

This phase significantly strengthened the server’s security posture by enforcing encrypted authentication, limiting network exposure, and applying least-privilege access. Performing all configuration via SSH reinforced best practices for real-world server administration and minimized direct console dependency.


