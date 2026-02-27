# DAY 4 — Group Policy Management & Enforcement  
**Project:** SecureCorp IT Support / Windows Server Administration  
**Environment:**  
- Windows Server 2022 (Domain Controller)  
- Windows 10/11 Client (Domain Joined)  
- Active Directory Domain Services (AD DS)

---

## 🎯 Objective
To design, configure, link, and test **Group Policy Objects (GPOs)** that enforce organizational security and desktop control policies on domain-joined client systems.

---

## 🛠 Tools Used
- Group Policy Management Console (GPMC)
- Active Directory Users and Computers (ADUC)
- Windows Command Prompt
- Domain-joined Windows Client

---

## 📌 DAY 4 Tasks Completed
- Create Password Policy GPO  
- Create Account Lockout Policy GPO  
- Create USB / Removable Storage Block GPO  
- Create Desktop Restriction GPO  
- Link GPOs to Organizational Units (OUs)  
- Test and verify GPO enforcement on client machine  

---

## 1️⃣ Opening Group Policy Management Console
**Purpose:** Manage all Group Policy Objects centrally.

### Steps:
1. Login to **Windows Server 2022 (Domain Controller)**
2. Click **Start Menu**
3. Search for **Group Policy Management**
4. Open the console

📸 **Screenshot:**  
`GroupPolicyManagement_Open.png`

---

## 2️⃣ Password Policy Configuration
**Purpose:** Enforce strong passwords across the domain.

### Steps:
1. In **Group Policy Management**
2. Right-click **Default Domain Policy**
3. Click **Edit**

📸 **Screenshot:**  
`Edit_DefaultDomainPolicy.png`

4. Navigate to:  

Computer Configuration
└─ Policies
└─ Windows Settings
└─ Security Settings
└─ Account Policies
└─ Password Policy


5. Configure:
- Minimum password length  
- Password complexity enabled  
- Maximum password age  
- Enforce password history  

📸 **Screenshots:**  
- `PasswordPolicy_Settings.png`  
- `Password_Config.png`

---

## 3️⃣ Account Lockout Policy Configuration
**Purpose:** Protect against brute-force login attacks.

### Steps:
1. In the same **Default Domain Policy Editor**
2. Navigate to:

Computer Configuration
└─ Policies
└─ Windows Settings
└─ Security Settings
└─ Account Policies
└─ Account Lockout Policy


3. Configure:
- Account lockout threshold  
- Account lockout duration  
- Reset account lockout counter  

📸 **Screenshots:**  
- `Lockout_Config.png`  
- `AccountLockoutPolicy.png`

---

## 4️⃣ USB / Removable Storage Block GPO
**Purpose:** Prevent unauthorized data transfer via USB devices.

### Steps:
1. In **Group Policy Management**
2. Right-click **Group Policy Objects**
3. Select **New**
4. Name the GPO:  

USB_Block_GPO


📸 **Screenshot:**  
`USB_Block_GPO_Create.png`

5. Right-click the new GPO → **Edit**
6. Navigate to:

Computer Configuration
└─ Policies
└─ Administrative Templates
└─ System
└─ Removable Storage Access


7. Enable:
- All Removable Storage classes: Deny all access  

📸 **Screenshots:**  
- `RemovableStorage_Settings.png`  
- `RemovableStorage_Settings_Config.png`

---

## 5️⃣ Desktop Restriction GPO
**Purpose:** Limit user control over desktop and system settings.

### Steps:
1. Create a new GPO named:

Desktop_Restriction_Policy


2. Edit the GPO and navigate to:

User Configuration
└─ Policies
└─ Administrative Templates
└─ Control Panel


3. Enable:
- Prohibit access to Control Panel and PC Settings  

📸 **Screenshot:**  
`ControlPanel_Block.png`

4. Navigate to:

User Configuration
└─ Policies
└─ Administrative Templates
└─ Desktop


5. Configure:
- Hide desktop icons  
- Restrict right-click options  

📸 **Screenshots:**  
- `Desktop_Restriction_Policy.png`  
- `Desktop_Items_Hidden.png`

---

## 6️⃣ Linking GPOs to Organizational Units (OUs)
**Purpose:** Apply policies only to intended users or computers.

### Steps:
1. In **Group Policy Management**
2. Right-click the target **Organizational Unit**
3. Click **Link an Existing GPO**
4. Select the required GPOs:
- USB_Block_GPO  
- Desktop_Restriction_Policy  

📸 **Screenshot:**  
`GPO_Linked_to_OU.png`

---

## 7️⃣ Client-Side GPO Testing & Verification
**Purpose:** Confirm policies are enforced on domain-joined systems.

### Steps on Client Machine:
1. Login using a **domain user account**
2. Open **Command Prompt**
3. Run:
```cmd
gpupdate /force

Verify applied policies:

gpresult /r

Screenshot:
GPO_Applied_gpresult.png

| Policy              | Result                               |
| ------------------- | ------------------------------------ |
| Password Policy     | Weak passwords rejected              |
| Account Lockout     | Account locked after failed attempts |
| USB Block           | USB devices inaccessible             |
| Desktop Restriction | Control Panel blocked                |
| GPO Linking         | Successfully applied via OU          |

Final Outcome

All security and desktop control policies were successfully created, linked, and enforced

Policies verified using gpresult

Client behavior matched expected enterprise security standards

🏢 Enterprise Relevance

This implementation mirrors real-world corporate IT environments, covering:

Identity security

Endpoint protection

User restriction policies

Centralized policy enforcement
.