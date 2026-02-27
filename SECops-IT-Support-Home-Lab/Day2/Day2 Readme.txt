# Day 2 – Windows Server 2022 Installation & Domain Controller Setup

**Project:** SECops IT Support Home Lab  
**Day:** 2  
**Focus:** Windows Server Installation, Active Directory Domain Services (AD DS), Domain Controller Promotion, DNS Verification  

---

## ✅ Day 2 Task Status

- [x] Install Windows Server 2022  
- [x] Set hostname (SEC-DC01)  
- [x] Assign static IP address  
- [x] Install AD DS role  
- [x] Promote server to Domain Controller  
- [x] Verify DNS functionality  

---

## 🎯 Objective

The objective of Day 2 is to deploy and configure **Windows Server 2022** as a fully functional **Domain Controller** for the SecureCorp lab environment.  
This includes hostname standardization, static IP configuration, Active Directory Domain Services installation, domain creation, and DNS verification following enterprise best practices.

---

## 🧱 Lab Environment Overview

| Component | Details |
|--------|--------|
| Hypervisor | VirtualBox |
| Server OS | Windows Server 2022 |
| Server Name | SEC-DC01 |
| Domain Name | securecorp.local |
| Network Type | Internal Network |
| Server IP Address | 192.168.56.10 |
| DNS Server | Self (Domain Controller) |

---

## 1️⃣ Windows Server 2022 Installation

Windows Server 2022 was installed successfully on the virtual machine using the GUI installation option.

**Outcome:**
- Server boots successfully
- GUI-based management enabled
- Ready for role installation

📸 **Screenshot – Windows Server Installed**

![Windows Server Installed](Screenshot/_Server_Installed.png)

---

## 2️⃣ Hostname Configuration

The server hostname was configured according to enterprise naming conventions.

**Configured Hostname:**

SEC-DC01


**Why this is important:**
- Domain Controllers must have fixed, identifiable hostnames
- Helps with DNS resolution, logging, and troubleshooting

📸 **Screenshot – Hostname Configuration**

![Hostname Configuration](Screenshot/Hostname.png)

---

## 3️⃣ Static IP Address Configuration  

The **Domain Controller (DC)** and **Client/Member Server** were configured with **static IPv4 addresses** to ensure reliable DNS resolution, authentication, and seamless communication within the internal network.  

---

### 🔹 Domain Controller (SEC-DC01) – Static IP  
**Network Configuration:**  
- **IP Address:** 192.168.56.10  
- **Subnet Mask:** 255.255.255.0  
- **Default Gateway:** Not required (Internal Network)  
- **Preferred DNS:** 192.168.56.10  

**Why a static IP is mandatory for a Domain Controller:**  
- Prevents IP changes that can break Active Directory  
- Ensures DNS consistency  
- Guarantees stable authentication services  

📸 **Screenshot – DC Static IP Settings**  
![Static IP Settings](Screenshot/SEC-DC01_StaticIP_Settings.png)  

📸 **Screenshot – DC IP Configuration Verification**  
![IPConfig Verification](Screenshot/SEC-DC01_ipconfig_StaticIP.png)  

---

### 🔹 Client / Member Server (SEC-CL01) – Static IP  
**Network Configuration:**  
- **IP Address:** 192.168.56.11  
- **Subnet Mask:** 255.255.255.0  
- **Default Gateway:** Not required (Internal Network)  
- **Preferred DNS:** 192.168.56.10 (Domain Controller)  

**Why a static IP is important for clients/servers in a lab setup:**  
- Ensures stable connectivity to the Domain Controller  
- Prevents DHCP-related IP changes that may disrupt authentication  
- Provides predictable addressing for testing and troubleshooting  

📸 **Screenshot – Client Static IP Settings**  
![Client Static IP Settings](Screenshot/SEC-CL01_StaticIP_Settings.png)  

📸 **Screenshot – Client IP Configuration Verification**  
![Client IPConfig Verification](Screenshot/SEC-CL01_ipconfig_StaticIP.png)  

## 4️⃣ Active Directory Domain Services (AD DS) Installation

The **Active Directory Domain Services** role was installed using Server Manager.

**Role Installed:**
- Active Directory Domain Services (AD DS)

**Purpose of AD DS:**
- Centralized user and computer management
- Group and policy enforcement
- Required for Domain Controller functionality

📸 **Screenshot – AD DS Role Installed**

![AD DS Role Installed](Screenshot/ADDS_Role_Installed.png)

---

## 5️⃣ Domain Controller Promotion

The server was promoted to a **Domain Controller** by creating a new Active Directory forest.

**Domain Configuration Details:**

Domain Name: securecorp.local
Forest Functional Level: Windows Server 2022
Domain Functional Level: Windows Server 2022


**Result:**
- Server rebooted automatically
- Active Directory services enabled
- DNS installed automatically

📸 **Screenshot – AD DS Deployment Configuration**

![AD DS Deployment Configuration](Screenshot/SEC-DC01_ADDS_DeploymentConfig.png)

---

## 6️⃣ DNS Configuration & Verification

DNS was automatically installed and configured during the Domain Controller promotion.

### DNS Verification Performed
- Verified Forward Lookup Zone creation
- Confirmed domain name resolution using nslookup

📸 **Screenshot – DNS Forward Lookup Zone**

![DNS Forward Lookup Zone](Screenshot/DNS_Forward_Lookup_Zone.png)

📸 **Screenshot – DNS Resolution Test (nslookup)**

![NSLookup DNS Test](Screenshot/NSLookup_DNS_Test.png)

---

## ✅ Final Outcome

By the end of Day 2:

- Windows Server 2022 is fully installed and configured
- Server is promoted to **Domain Controller (SEC-DC01)**
- Active Directory Domain Services are operational
- DNS is functioning correctly
- Environment is ready for user, group, and GPO configuration

---

## 📌 Skills Demonstrated

- Windows Server 2022 Administration  
- Active Directory Domain Services (AD DS)  
- Domain Controller Deployment  
- DNS Configuration & Troubleshooting  
- Static IP & Enterprise Network Configuration  

---

> 📁 This documentation is part of the **SECops IT Support Home Lab** project and is maintained for learning, portfolio building, and professional demonstration purposes.
