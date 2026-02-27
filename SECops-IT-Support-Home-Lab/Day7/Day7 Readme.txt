# ☁️ Day 7: Microsoft Intune Device Management & Security Hardening

## 📌 Project Overview
In this phase of the **HOMELAB IT Project**, I transitioned from on-premises Active Directory management to Cloud-based Endpoint Management using **Microsoft Intune**. This module demonstrates the ability to enroll devices, enforce security compliance, and automate software deployment—critical skills for IT Support and SOC Analyst roles in the UAE market.

---

## 🏗️ Phase 1: Licensing & Environment Prep
Before managing devices, the environment must be correctly licensed to allow for MDM (Mobile Device Management) enrollment.

### 1. License Assignment
To enable mobile device management, the user account requires a specific license that includes Intune plan rights.
* **Action:** Assigned the **Microsoft 365 / Intune** license to the test user via the Admin Center.
* **Why it matters:** Without this, the user cannot enroll devices or receive company policies.
* **Evidence:**
    > ![Intune License Assignment](Intune-License-Assigned.png)

### 2. Company Portal Configuration
The Company Portal is the "Self-Service" hub for end-users to install apps and check compliance.
* **Action:** Installed and configured the **Company Portal** app on the client VM.
* **Why it matters:** It serves as the primary interface between the employee and the IT department for non-managed application requests.
* **Evidence:**
    > ![Company Portal Setup](Company-portal-setup.png)
    > ![Company Portal Login Success](Company-Portal-Login-Success.png)

---

## 💻 Phase 2: Device Enrollment (Entra ID Join)
Connecting the local Virtual Machine to the Cloud Tenant to establish management authority.

### 3. Entra ID Join Process
This step involves the formal "handshake" between the local Windows 11 OS and the Microsoft Entra ID (Azure AD) tenant.

**🛠️ Step-by-Step Execution:**
1.  **Initiation:** On the Windows 11 VM, I navigated to **Settings > Accounts > Access work or school**.
2.  **Connection:** Clicked **Connect**. Crucially, I selected the link **"Join this device to Microsoft Entra ID"** (at the bottom) rather than just signing in. This distinction is vital for full device management versus simple app registration.
3.  **Authentication:** Signed in using the licensed test user credentials created in Day 5.
4.  **Auto-Enrollment:** Because the MDM scope was configured in Entra ID, the device automatically enrolled into Intune immediately after the join.
5.  **Verification:** The device status changed to **"Connected to [Tenant Name] MDM"**, confirming successful enrollment.

* **Evidence:**
    > ![Device Enrollment Success](Device_Enrollment_Success.png)

---

## 🛡️ Phase 3: Security & Compliance Policies
Defining "Health" standards and enforcing security restrictions via Cloud Policy (the modern equivalent of GPOs).

### 4. Device Compliance Policy
Created a baseline policy to ensure devices meet specific security health standards before accessing company resources.
* **Configuration:**
    * **Health:** Required **BitLocker** encryption and Secure Boot.
    * **Security:** Enforced **Microsoft Defender Antivirus** (Real-time protection).
    * **Password:** Enforced a **Minimum Password Length** of 8 characters.
* **Outcome:** If a device fails these checks, it is marked "Non-Compliant" and can be blocked from accessing email (Conditional Access).
* **Evidence:**
    > ![Compliance Policy Configuration](Compliance_Policy_Configure.png)
    > ![Compliance Policy Final Review](Compliance_Policy_Final.png)

### 5. Configuration Profile (Security Baseline)
Used the **Settings Catalog** to enforce organizational settings that harden the OS.
* **Key Action:** Blocked **Manual MDM Unenrollment**.
* **Why it matters:** This prevents users from "going rogue" by removing the management profile to bypass security rules.
* **Evidence:**
    > ![Configuration Profile Basics](Configuration_Profile_Basics.png)

### 6. USB Storage Restriction (Data Loss Prevention)
Implemented a high-value security policy to block unauthorized USB storage devices, a common requirement in banking and government sectors.
* **Mechanism:** Used **Administrative Templates** (Device Control).
* **Setting:** Enabled *"All Removable Storage classes: Deny all access"*.
* **Result:** When a USB drive is inserted, Windows immediately blocks read/write access and displays an "Access Denied" notification.
* **Evidence:**
    > ![USB Block Policy Configuration](USB_Block_Policy_Config.png)

---

## 📦 Phase 4: Automated App Deployment
Modernizing software delivery by moving away from manual installers and "Gold Images."

### 7. Microsoft 365 Apps (Teams)
Configured the M365 app suite to push productivity tools automatically.
* **Settings:**
    * **Update Channel:** Monthly Enterprise Channel (for stability).
    * **Assignment:** Set to **Required** (Forces silent installation).
* **Why it matters:** Ensures all employees have the exact same version of office tools without manual IT intervention.
* **Evidence:**
    > ![M365 App Configuration](M365_App_Configuration.png)

### 8. Google Chrome Enterprise (MSI Deployment)
Since Chrome is not native to the Microsoft Store, I deployed it as a **Line-of-Business (LOB)** app.
* **Method:** Uploaded the official **Google Chrome Enterprise .msi** installer.
* **Configuration:** Enabled **"Ignore app version"** to allow the browser to update itself via Google Update services, reducing administrative overhead.
* **Evidence:**
    > ![Chrome MSI Deployment](Chrome_MSI_Deployment.png)

---

## 🏁 Summary of Day 7 Skills
| Domain | Skill Demonstrated |
| :--- | :--- |
| **Endpoint Management** | Intune Device Enrollment & Lifecycle Management |
| **Identity** | Microsoft Entra ID Join & User Assignment |
| **Security Hardening** | Attack Surface Reduction (USB Blocking, Antivirus) |
| **App Delivery** | Packaging MSI apps & deploying M365 Suites |
| **Compliance** | Defining and enforcing corporate health standards |

---