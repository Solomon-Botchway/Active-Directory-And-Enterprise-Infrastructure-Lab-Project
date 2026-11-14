# SoloTech Innovations Enterprise Active Directory Lab

## Overview

SoloTech Innovations is a hands-on enterprise infrastructure lab designed to simulate a real-world Microsoft environment using Hyper-V, Windows Server 2022, and Windows 11 Enterprise.

The project focuses on building practical experience in:
- Active Directory Domain Services (AD DS)
- DNS Administration
- Group Policy Management
- Identity & Access Management (IAM)
- File and Print Services
- Software Deployment
- Windows Event Forwarding (WEF)
- Scheduled Task Automation
- Security Monitoring
- IT Service Management
- Enterprise Troubleshooting

The environment was designed, deployed, administered, and continuously improved through real-world support scenarios and change-management style projects.

---
<img width="806" height="467" alt="Screenshot 2026-11-07 062552" src="https://github.com/user-attachments/assets/b570938a-e8c1-4029-8e92-f1665e936d09" />

<img width="753" height="448" alt="image" src="https://github.com/user-attachments/assets/e818a17d-faf6-4b8c-a317-11063b6da686" />


<img width="1066" height="1053" alt="Screenshot 2026-10-16 045937" src="https://github.com/user-attachments/assets/5274949b-cdfd-43ba-874e-ff004338a22a" />

# Infrastructure Overview

```text
                                            INTERNET
                                                │
                                       Home Router / WiFi
                                                │
                            ┌───────────────────┴───────────────────┐
                            │                                       │
                          Host Laptop                         HP DJ2700 Series Printer
                     HP Elitebook Windows 11 Pro                  (On-Site)
                                │
                   Hyper-V Internal LAB Switch 
                      + External Switch 
                                │
    ┌───────────────────────────┼───────────────────────┼────────────────────────────┐
    │                           │                       │                            │
  DC01                        FS01                     PC01/03                         PC02
Windows Server              Windows Server          Windows 11                 Linux Ubuntu 26.04
2022 Enterprise             2022 Enterprise          Workstation                   Workstation
(Administrators)            (Domain Admins)           (All Users)                 (IT-Team Only)
       │                         │
       ▼                         ▼
  Active Directory           Department Shares/Drives Mapping
  DNS                        User Home Folders
  DHCP                       Archive Storage
  GPO                        Software Repository
  Printer Deployment         Wallpaper Repository
  Event Log Collector        Screensaver Repository

        │                          │                              │                              │
        └──────────────────────────────── solotech.local ────────────────────────────────────────┘
                                    Centralized Authentication

```
## Active Directory Structure
<img width="556" height="389" alt="Screenshot 2026-11-07 062831" src="https://github.com/user-attachments/assets/329a58fd-62f4-4ca1-b0b4-cc697bf68186" />

```
solotech.local

└── SoloTech
    ├── IT
    ├── HR
    ├── Finance
    ├── Sales
    └── Customer Service
```

### Security Groups
```
IT-Team
HR-Team
Finance-Team
Sales-Team
CustomerService-Team
Finance-Team-Payroll
Automation-Robotics
```
<img width="792" height="565" alt="Screenshot 2026-10-16 045616" src="https://github.com/user-attachments/assets/f0735ca1-e0b5-4c40-b2bd-9f5f0545805a" />

---
# Infrastructure Components

## DC01 & FS01– Windows Server 2022

Configured as the central infrastructure server providing:

- Active Directory Domain Services (AD DS)
- DNS
- DHCP
- Group Policy Management
- File Services
- Storage Services
- Print Services
- Software Deployment Repository
- Windows Event Collector
- 
<img width="808" height="434" alt="Screenshot 2026-11-07 060929" src="https://github.com/user-attachments/assets/9767a221-a104-46f9-86b5-87588d19a143" />

## PC01 & PC03 – Windows 11 Enterprise

Configured as the primary domain-joined workstation for:
<img width="806" height="692" alt="Screenshot 2026-10-12 004540" src="https://github.com/user-attachments/assets/192a1776-e6e9-458c-beef-fd53bb742da2" />

- User authentication testing
- Group Policy validation
- Software deployment testing
- Printer deployment testing
- Security monitoring
- Event forwarding

## PC02 – LINUX UBUNTU 26.04

 Domain-joined workstation for:

- RBAC authentication testing
- Multi-Platform testing
<img width="515" height="448" alt="Screenshot 2026-10-04 202507" src="https://github.com/user-attachments/assets/fb90b7fb-16e7-4847-a568-a6eb21ed434c" />

<img width="527" height="473" alt="Screenshot 2026-10-04 2026331" src="https://github.com/user-attachments/assets/fa244342-7928-4802-8629-6e19db76350d" />

---

# Core Technologies Implemented

## 1. Active Directory & Identity Management
<img width="795" height="410" alt="Screenshot 2026-11-07 071449" src="https://github.com/user-attachments/assets/054f4038-d964-482a-887f-ccec8ac232e4" />

- User account provisioning
- Password management
- Account lockout policies
- Department-based Organizational Units
- Security Group administration
- Role-Based Access Control (RBAC)
- Least Privilege implementation

## 2. DNS (Domain Name System)
<img width="956" height="415" alt="image" src="https://github.com/user-attachments/assets/5e8a8183-b79d-4526-a591-ad69242ea492" />


Implemented and managed Microsoft DNS as part of the Active Directory infrastructure on DC01.

### Key Responsibilities

- Installed and configured the DNS Server role
- Integrated DNS with Active Directory Domain Services (AD DS)
- Managed the internal DNS zone:


```text
solotech.local
```

- Verified domain name resolution between servers and clients
- Supported Active Directory authentication and Group Policy processing
- Configured DNS records for domain-joined devices
- Performed DNS troubleshooting and record management
- Implemented DNS forwarding to external ISP DNS servers for internet name resolution

### Enterprise Features Demonstrated

- Active Directory Integrated DNS
- Forward and Reverse Lookup Zones
- Dynamic DNS Registration
- DNS Forwarders
- Name Resolution Troubleshooting
- Client and Server DNS Configuration

### Example Environment

```text
DC01
192.168.10.10
DNS Server

FS01
192.168.10.20

PC01
192.168.10.110

PC02
Linux Workstation

PC03
192.168.10.130
```

All systems use:

```text
192.168.10.10
```

as their primary DNS server, ensuring consistent domain authentication, Group Policy application, drive mapping, file server access, and resource discovery throughout the environment.

### Skills Demonstrated

- Microsoft DNS Administration
- Active Directory Integration
- Name Resolution
- DNS Forwarders
- DNS Troubleshooting
- Enterprise Network Services
---

## 3. DHCP Implementation
<img width="784" height="330" alt="Screenshot 2026-10-19 005508" src="https://github.com/user-attachments/assets/59e8c2fe-d450-4c3b-a12a-9630410a752c" />


A centralized DHCP service was deployed on DC01 to automate IP address management.

### Scope Configuration

```text
Scope:
192.168.10.100 - 192.168.10.200

Domain:
solotech.local

DNS:
192.168.10.10

Router:
192.168.0.1
```

### Reservations

```text
PC01
192.168.10.110

PC03
192.168.10.130

FS01
192.168.10.20
```

### Benefits

- Centralized endpoint management
- Consistent IP allocation
- Automatic DNS registration
- Reduced manual configuration
- Enterprise-style network administration
<img width="512" height="386" alt="Screenshot 2026-10-18 235322" src="https://github.com/user-attachments/assets/8e793563-7412-491e-9c53-5a68f7e13fce" />

### Skills Demonstrated

- Windows DHCP Administration
- Scope Management
- DHCP Reservations
- DNS Integration
- Network Infrastructure Management
---

## 4. Group Policy Management
<img width="957" height="515" alt="image" src="https://github.com/user-attachments/assets/a7d5671f-9d1a-4445-a337-aae3bd49f872" />

Successfully implemented:
<img width="590" height="382" alt="Screenshot 2026-09-24 180054" src="https://github.com/user-attachments/assets/08322fb4-201e-40f2-926e-cdc06a2a75b4" />

- Password Complexity Policies
- Account Lockout Policies
- Department Drive Mapping
- Department Printer Deployment
- HR Wallpaper Deployment
- Customer Service Restrictions
- Software Deployment
- Security Auditing Policies
- Finance only Software
- Finance Desktop Policies
<img width="966" height="1017" alt="image" src="https://github.com/user-attachments/assets/cb081a92-2303-45d2-b539-07d8e534a5e3" />

<img width="506" height="501" alt="image" src="https://github.com/user-attachments/assets/bcd856a8-013b-425d-bca8-1739aaeb2fc3" />

## HR Wallpaper Deployment by GPO
<img width="511" height="448" alt="Screenshot 2026-09-26 041545" src="https://github.com/user-attachments/assets/078ed599-6c83-4fd4-ab46-31347651b9c0" />


## 5. File Services
<img width="812" height="539" alt="Screenshot 2026-11-07 062347" src="https://github.com/user-attachments/assets/d9906eda-4915-41fc-963a-c301c65e4014" />

Departmental file shares secured through:

- Active Directory Security Groups
- Share Permissions
- NTFS Permissions
- Least Privilege Design

```
Examples:

IT_Drive

HR_Drive

FINANCE_Drive

SALES_Drive

CUST-SERV_Drive
```
<img width="1045" height="898" alt="Screenshot 2026-09-29 020024" src="https://github.com/user-attachments/assets/f7ea2c29-be1d-4125-89b1-7255d8a6b13e" />

A separate Payroll security model was implemented using:

```text
Finance-Team-Payroll
```

to protect sensitive financial records.

---
# Featured Projects

## 1. New Employee Onboarding
<img width="1046" height="491" alt="Screenshot 2026-10-11 034410" src="https://github.com/user-attachments/assets/eac439fe-8c60-4dab-956c-d29700621531" />

### Ticket Reference

INC-003 – Finance Assistant Onboarding

### Business Requirement

Provision a new Finance employee with:

- Finance drive access
- Finance printer access
- Standard domain access

Restrictions:

- No Payroll access
- No access to other departments
- No access to other departmental printers

### Provisioning Activities

Created and configured:

```text
solotech.local
└── SoloTech
    └── Finance
         └── emma.hughes
```

Configured:

- Temporary password
- Mandatory password change at first logon
- Department information
- Job title
- Manager
- Office location

Assigned Groups:

```text
Domain Users
Finance-Team
```

### Security Implementation

Created:

```text
Finance-Team-Payroll
```

to isolate Payroll data.

The new employee was deliberately excluded from Payroll access using:

- NTFS permissions
- Security groups
- RBAC principles

### Validation Results

| Resource | Result |
|-----------|---------|
| Finance Drive | ✅ Accessible |
| Finance Documents | ✅ Read & Write |
| Payroll Folder | ❌ Access Denied |
| Finance Printer | ✅ Accessible |
| Other Departments | ❌ Access Denied |

### Skills Demonstrated

- User Provisioning
- RBAC
- Active Directory Administration
- NTFS Permissions
- Least Privilege
- Service Desk Documentation

---

## 2. Security Monitoring & Event Forwarding
![Uploading Screenshot 2026-09-30 225853.png…]()
<img width="766" height="380" alt="Screenshot 2026-09-30 225739" src="https://github.com/user-attachments/assets/cef09553-387f-49f9-84b2-15382335ed71" />

### Objective

Implement centralized event collection and security auditing.
<img width="956" height="415" alt="image" src="https://github.com/user-attachments/assets/479b2c93-ad2c-4227-918d-39ab4447ddd2" />

<img width="565" height="463" alt="Screenshot 2026-09-30 224737" src="https://github.com/user-attachments/assets/2a38dccf-9d35-4f98-ab8c-de32ae03ca37" />

### Architecture
<img width="850" height="520" alt="Screenshot 2026-09-30 224946" src="https://github.com/user-attachments/assets/7ee4839b-6581-406a-8a17-c9fddc3bd5d2" />

```text
PC01
    ↓
Windows Event Forwarding (WEF)
    ↓
DC01 Event Collector
```

### Events Monitored

- Successful Logons (4624)
- Failed Logons (4625)
- Account Lockouts (4740)
- User Account Changes
- Security Group Changes

### Security Controls Implemented

- Windows Event Forwarding
- Subscription Management
- Firewall Configuration
- Security Auditing via GPO
- Centralized Event Collection

### Security Benefit

Provides visibility into:

- Authentication activity
- Account management events
- Security policy enforcement
- User behaviour monitoring
<img width="571" height="437" alt="Screenshot 2026-09-30 223545" src="https://github.com/user-attachments/assets/be9da7d2-44b9-4aba-ba97-67d3b7bb2f69" />

<img width="478" height="286" alt="Screenshot 2026-09-30 224542" src="https://github.com/user-attachments/assets/9a2fde9c-147f-4a06-b2af-a0d6c309f4d3" />

---

# Troubleshooting Experience

Throughout the project, multiple enterprise-style incidents were investigated and resolved.

### Resolved Issues

- Windows 11 TPM and Secure Boot deployment failures
- Active Directory trust relationship failures
- GPO Security Filtering issues
- Drive mapping failures
- Printer deployment failures
- Default printer assignment issues
- Account lockout investigations
- Group Policy delegation issues
- Software deployment failures
- Windows Event Forwarding configuration issues
- DNS-related authentication issues
- Hyper-V Enhanced Session behaviour

Each issue was documented using:

- Investigation
- Root Cause Analysis
- Resolution
- Validation
- Lessons Learned

---

# General Technical Skills Demonstrated

## Infrastructure

- Windows Server 2022
- Windows 11 Enterprise
- Hyper-V
- DNS
- Active Directory Domain Services

## Identity & Access Management

- User Provisioning
- Security Groups
- Role-Based Access Control (RBAC)
- Least Privilege
- User Lifecycle Management

## Group Policy

- GPO Design
- Security Filtering
- Delegation
- Drive Mapping
- Printer Deployment
- Software Deployment

## Security

- Windows Event Forwarding
- Security Auditing
- Account Lockout Monitoring
- Event Analysis
- Access Control

## IT Operations

- Incident Management
- Troubleshooting
- Service Desk Documentation
- Root Cause Analysis
- Change Validation

---

# Key Outcomes

This project evolved from a simple Active Directory deployment into a miniature enterprise infrastructure environment incorporating:

✅ Identity Management

✅ Access Control

✅ Group Policy Automation

✅ File & Print Services

✅ Software Distribution

✅ Security Monitoring

✅ User Lifecycle Management

✅ IT Service Management

✅ Cyber Security Foundations

---


## 3. Scheduled Task Authentication & Network Drive Troubleshooting
<img width="1069" height="1000" alt="Screenshot 2026-10-10 124358" src="https://github.com/user-attachments/assets/4b7872a7-58ca-4fa5-8e66-daba97fad6c4" />

### Overview

As part of my Active Directory Helpdesk Lab, I created and tested a Scheduled Task running under a domain user account (`SOLOTECH\d.carter`) to simulate a real-world account lockout scenario caused by stale credentials.

During implementation, I encountered and resolved several issues involving Group Policy, Windows authentication, Task Scheduler security contexts, and mapped network drives. This exercise provided practical experience troubleshooting Windows administration issues commonly seen in enterprise environments.


<img width="1014" height="868" alt="Screenshot 2026-10-11 210916" src="https://github.com/user-attachments/assets/25c3eaf9-5d1f-4755-80e7-f05f1abb1180" />

---

### Objective

Create an automated reporting task that runs under a domain account and writes report data to a department file share.

---

### Issue 1: Scheduled Task Would Not Start
<img width="522" height="237" alt="Screenshot 2026-10-10 144836" src="https://github.com/user-attachments/assets/434672f8-dc13-4a0f-87e0-8fd76f02d2ec" />
#### Symptoms

The task failed to execute and displayed:

```text
This task requires that the user account specified has
Log on as a batch job rights.
```
<img width="641" height="808" alt="Screenshot 2026-10-10 200038" src="https://github.com/user-attachments/assets/95e643ca-47f2-489f-904a-2151ffadc29a" />
#### Root Cause

Although the user account could log on interactively, Task Scheduler runs under a separate **batch logon** security context requiring the **Log on as a batch job** user right.

#### Resolution


Configured the required User Rights Assignment through Group Policy and applied updates using:

```cmd
gpupdate /force
```

#### Skills Demonstrated

- Group Policy Management
- User Rights Assignment
- Windows Authentication
- Task Scheduler Administration

---

### Issue 2: Verifying Task Execution

#### Test

```cmd
whoami > C:\Temp\report.txt
```

#### Result

The Scheduled Task completed successfully and generated:

```text
solotech\d.carter
```

confirming that the task was executing under the intended domain account.

#### Skills Demonstrated

- Task Validation
- Windows Command Line
- Security Context Verification

---
<img width="1022" height="847" alt="Screenshot 2026-10-10 185133" src="https://github.com/user-attachments/assets/76267849-bd0d-4436-bf3a-10b31cc8a333" />

### Issue 3: Scheduled Task Failed When Writing to Mapped Network Drive

#### Test

```text
F:\Notes\report.txt
```

#### Result

Task Scheduler returned:

```text
0x1
```

The same command executed successfully when run manually from PowerShell or Command Prompt.

---

### Investigation

To identify the difference, I compared the output of:

```cmd
net use
```

#### Interactive User Session

```text
F: mapped to Finance Department Drive
```

#### Scheduled Task Session

```text
There are no entries in the list.
```

---

### Root Cause

The mapped drive letter (`F:`) existed only within the user's interactive logon session.

When Task Scheduler executed under a batch logon session, mapped network drives were unavailable, causing the task to fail when attempting to access the share using the drive letter.

---

### Resolution

Replaced the mapped drive path:

```text
F:\Notes\report.txt
```

with the UNC path:

```text
\\DC01\Finance_Data\Notes\report.txt
```

The task immediately executed successfully and wrote the report to the shared 

## Future Enhancements

Planned expansion areas include:

- Microsoft 365 Administration
- Microsoft Entra ID
- Microsoft Intune
- Microsoft Sentinel
- PowerShell Automation
- Vulnerability Management
- Security Operations Centre (SOC) Workflows
- Incident Response Scenarios
