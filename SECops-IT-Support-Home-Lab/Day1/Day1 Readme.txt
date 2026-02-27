# Day 1 – Virtualization & Networking

**Project:** SecureCorp IT Support Home Lab.
**Date:** 14-01-2026  
**Objective:** Set up a virtualized lab environment using Oracle VirtualBox, configure virtual networks, deploy Windows Server 2022 and Windows 10/11 VMs, and test connectivity between them.

---

## 1. Tools & Software Used

| Tool / Software           | Purpose                                     |
|---------------------------|---------------------------------------------|
| Oracle VirtualBox         | Virtualization platform                     |
| Windows Server 2022       | Server VM                                   |
| Windows 10/11             | Client VM                                   |
| NAT Network Adapter       | Internet access for VMs                     |
| Internal Network Adapter  | VM-to-VM communication                      |
| ipconfig, ping            | Network testing commands                    |
| Draw.io / Lucidchart      | Network diagram                             |

---

## 2. Step-by-Step Execution

### Step 1 — Install Oracle VirtualBox
**Purpose:** To create a virtualization platform for deploying and testing server/client VMs.  
**Steps:**
1. Download Oracle VirtualBox from the official website.
2. Run the installer and complete setup.
3. Launch VirtualBox and verify installation.

**Screenshot:**  
`![Installation Screenshot](screenshots/install_OracleVirtualBox.png)`

---

### Step 2 — Create Virtual Network Adapters

#### 2.1 NAT Adapter
**Purpose:** Provides Internet access to VMs via host machine.  
**Steps:**
1. Open VirtualBox → Settings → Network → Add NAT Adapter.
2. Assign to VM under Network → Adapter 1 → Attached to: NAT.
3. Enable cable connection.

**Screenshot:**  
`![NAT Switch](screenshots/nat_switch.png)`

#### 2.2 Internal Network Adapter
**Purpose:** Enables communication between VMs without external access.  
**Steps:**
1. Go to VM Settings → Network → Adapter 2 → Attached to: Internal Network.
2. Name: `Internal_Switch`.
3. Enable cable connection.

**Screenshot:**  
`![Internal Switch](screenshots/internal_switch.png)`

---

### Step 3 — Create Windows Server 2022 VM
**Purpose:** Deploy a server VM for client testing and network services.  
**Steps:**
1. Click "New" → Name: `Server_VM` → Assign CPU, RAM, Disk.
2. Attach Windows Server 2022 ISO.
3. Configure Adapter 1 (NAT) and Adapter 2 (Internal).
4. Install OS and configure IP settings.

**Screenshot:**  
`![Server VM](screenshots/server_vm.png)`

---

### Step 4 — Create Windows 10/11 Client VM
**Purpose:** Deploy a client VM to test connectivity and simulate user endpoints.  
**Steps:**
1. Click "New" → Name: `Client_VM` → Assign resources.
2. Attach Windows 10/11 ISO.
3. Configure Adapter 1 (NAT) and Adapter 2 (Internal).
4. Install OS and configure IP settings.

**Screenshot:**  
`![Client VM](screenshots/client_vm.png)`

---

### Step 5 — Test Connectivity

#### 5.1 IP Configuration Check
**Command:**
```cmd
ipconfig

---

## Step 6 — Network Diagram

**Purpose:** Visualize how the Server and Client VMs are connected inside Oracle VirtualBox using NAT and Internal Network adapters. This diagram represents the exact setup used in Day 1, including the NAT‑assigned IP address **10.0.2.15**.

### Network Diagram (ASCII)

                           +----------------------+
                           |      Internet        |
                           +----------+-----------+
                                      |
                                      | NAT
                                      |
                     +----------------v----------------+
                     |        Host Machine             |
                     |       (Windows 11 Laptop)       |
                     +----------------+----------------+
                                      |
        -----------------------------------------------------------------
        |                                                               |
        | NAT Network (Adapter 1)                                       |
        | Internal Network (Adapter 2)                                  |
        -----------------------------------------------------------------
                                      |
        -----------------------------------------------------------------
        |                                                               |
+---------------------------+                         +---------------------------+
|     Windows Server 2022   |                         |     Windows 10/11 Client  |
|         (Server_VM)       |                         |        (Client_VM)        |
|---------------------------|                         |---------------------------|
| Adapter 1: NAT            |                         | Adapter 1: NAT            |
| Adapter 2: Internal       |                         | Adapter 2: Internal       |
| IP (NAT): 10.0.2.15       |                         | IP (NAT): 10.0.2.15       |
| IP (Internal): Assigned   |                         | IP (Internal): Assigned   |
+---------------------------+                         +---------------------------+



### Explanation
- **NAT Adapter** gives both VMs Internet access through the host.  
- **Internal Network Adapter** allows Server and Client to communicate privately.  
- Both VMs receive the default VirtualBox NAT IP **10.0.2.15**.  
- Internal network IPs will be assigned manually or via DHCP depending on your setup.  
- This architecture simulates a real corporate environment with isolated internal traffic plus external Internet access.

---