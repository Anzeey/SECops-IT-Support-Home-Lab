# Day 6 — Azure AD Connect & MFA Configuration  
**IT Infrastructure & Support Lab — Documentation**

---

## 1. Overview

**Objective:**  
Configure hybrid identity using Azure AD Connect and secure cloud sign‑ins with MFA.

**Environment:**  
- **On‑Prem Server:** SEC-DC01 (AD DS + DNS)  
- **Cloud:** Microsoft 365 Developer Tenant (Entra ID)  
- **Tasks Completed:**  
  - Install Azure AD Connect  
  - Sync AD users to Microsoft 365  
  - Enable MFA  
  - Test MFA login  
  - Simulate MFA lockout  
  - Reset MFA as admin  

**Screenshots Referenced:**  
- `ConnectSync-Selected.png`  
- `DecommissionDownloadCentre.png`  
- `Manual_Sync_Command.png`  
- `MFA_Code_Approved.png`  
- `MFA_Enabled_For_Users.png`  
- `MFA_Lockout_Simulation.png`  
- `MFA_Login_Test_Success.png`  
- `MFA_Reset_By_Admin.png`  
- `MFA_Setup_Required.png`  
- `OnPrem_AD_Admin_Login.png`  
- `Sync_Configuration_Success.png`  
- `User_Sync_Verified.png`

---

## 2. Prerequisites & Initial Validation

### 2.1 Log in to Domain Controller  
- Logged into **SEC-DC01** using Domain Admin credentials.  
- **Screenshot:** `OnPrem_AD_Admin_Login.png`

### 2.2 Validate Active Directory  
- Open **Active Directory Users and Computers**  
- Confirm:  
  - Domain structure  
  - OUs created on Day 3  
  - 25–30 users exist and are enabled  

### 2.3 Validate DNS  
- Ensure SEC-DC01 resolves external domains  
- Confirm Microsoft 365 tenant domain resolves correctly  

---

## 3. Install Azure AD Connect

### 3.1 Download Installer  
- Downloaded Azure AD Connect from Microsoft official site  
- Saved under `C:\Install\AzureADConnect`

### 3.2 Run Installer  
- Right‑click → **Run as Administrator**  
- Accepted license terms  

### 3.3 Choose Installation Type  
- Selected **Express Settings**  
- Selected **Password Hash Synchronization**  
- **Screenshot:** `ConnectSync-Selected.png`

### 3.4 Provide Credentials  
- Entered **Enterprise Admin** credentials for on‑prem AD  
- Entered **Global Admin** credentials for Microsoft 365  

### 3.5 Complete Configuration  
- Reviewed summary  
- Clicked **Install / Configure**  
- **Screenshot:** `Sync_Configuration_Success.png`

---

## 4. Verify Directory Synchronization

### 4.1 Initial Sync  
- Azure AD Connect automatically performed first sync  

### 4.2 Manual Sync  
Opened PowerShell as Administrator and ran:

Start-ADSyncSyncCycle -PolicyType Delta


- **Screenshot:** `Manual_Sync_Command.png`

### 4.3 Verify Users in Microsoft 365  
- Microsoft 365 Admin Center → Users → Active Users  
- Confirmed users show as **Synced from Active Directory**  
- **Screenshot:** `User_Sync_Verified.png`

### 4.4 Decommission Old Sync Tools (If Any)  
- Documented removal of older sync tools  
- **Screenshot:** `DecommissionDownloadCentre.png`

---

## 5. Enable MFA for Synced Users

### 5.1 Open MFA Settings  
- Microsoft 365 Admin Center → Users → Per‑User MFA  

### 5.2 Enable MFA  
- Selected synced users  
- Set MFA status to **Enabled / Enforced**  
- **Screenshot:** `MFA_Enabled_For_Users.png`

### 5.3 Force MFA Registration  
- Enabled “Require MFA registration at next login”  
- **Screenshot:** `MFA_Setup_Required.png`

---

## 6. Test MFA Login

### 6.1 User Sign‑In  
- On Windows 10/11 client → browser → `portal.office.com`  
- Signed in using synced AD user credentials  

### 6.2 MFA Registration  
- User prompted to configure MFA  
- **Screenshot:** `MFA_Setup_Required.png`

### 6.3 Approve MFA Challenge  
- Approved via Microsoft Authenticator  
- **Screenshot:** `MFA_Code_Approved.png`

### 6.4 Successful Login  
- User successfully logged into Microsoft 365  
- **Screenshot:** `MFA_Login_Test_Success.png`

---

## 7. Simulate MFA Lockout

### 7.1 Trigger Lockout  
- Entered incorrect MFA codes repeatedly  
- Removed MFA method to force failure  

### 7.2 Lockout Behavior  
- User blocked from accessing Microsoft 365  
- **Screenshot:** `MFA_Lockout_Simulation.png`

---

## 8. Reset MFA as Administrator

### 8.1 Admin Access  
- Logged in as Global Admin  
- Microsoft 365 Admin Center → Users → Authentication Methods  

### 8.2 Reset MFA  
- Selected **Require re‑register MFA**  
- **Screenshot:** `MFA_Reset_By_Admin.png`

### 8.3 User Re‑Registration  
- User signs in again  
- MFA setup required again  
- Login successful after approval  
- **Screenshots:**  
  - `MFA_Setup_Required.png`  
  - `MFA_Code_Approved.png`  
  - `MFA_Login_Test_Success.png`

---

## 9. Summary of Skills Demonstrated

- Hybrid identity configuration (Azure AD Connect)  
- Directory synchronization troubleshooting  
- MFA security implementation  
- MFA lockout simulation & recovery  
- Real‑world IT support workflow  
- Evidence‑based documentation with screenshots  

---
