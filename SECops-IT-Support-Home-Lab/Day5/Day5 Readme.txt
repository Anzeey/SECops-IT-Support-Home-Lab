# VS Code Markdown Project for Day 5 Microsoft 365 Documentation

# Folder Structure
# DAY5_M365_Documentation/
# │
# ├─ screenshots/
# │   ├─ Exchange_Admin_Login_Success.png
# │   ├─ M365_Admin_Center_Dashboard.png
# │   ├─ M365_License_Overview.png
# │   ├─ M365_Users_Created.png
# │   ├─ Outlook_Email_Test.png
# │   ├─ Microsoft_Teams_Configured.png
# │   └─ OneDrive_File_Uploaded.png
# │
# └─ Day5_M365_Documentation.md

# Markdown File: Day5_M365_Documentation.md
markdown_content = '''
# DAY 5 — Microsoft 365 Tenant Setup (Business Standard Trial)

## Project Context
This documentation covers **Day 5** of the SecureCorp IT Support & Systems Administration Lab. The objective of this day was to set up and validate a **Microsoft 365 cloud tenant** using a **Microsoft 365 Business Standard Trial**, create users, assign licenses, configure core collaboration services, and verify administration access through Microsoft admin portals.

This simulates a **real enterprise onboarding and cloud service setup** performed by IT Support / System Administrators.

---

## Objectives of Day 5

* Create and access a Microsoft 365 tenant
* Verify license availability
* Create cloud users (employees)
* Assign Microsoft 365 licenses
* Configure and test:
  * Outlook (Exchange Online)
  * Microsoft Teams
  * OneDrive for Business
* Access Exchange Admin Center to verify mailbox provisioning

---

## Environment Used

* **Tenant Type:** Microsoft 365 Business Standard (Trial)
* **Admin Role:** Global Administrator
* **Access Method:** Microsoft 365 Admin Center (Web)

---

## Step 1: Access Microsoft 365 Admin Center

### How It Was Done:
1. Opened browser and navigated to **[https://admin.microsoft.com](https://admin.microsoft.com)**
2. Logged in with the **Global Admin account** created during tenant setup
3. Confirmed that the dashboard loaded correctly, showing Users, Billing, Teams, and Admin Centers

**Why:** To verify that the Microsoft 365 tenant is active and accessible for administration

**Screenshot:**
* `M365_Admin_Center_Dashboard.png`

---

## Step 2: Verify License Availability

### How It Was Done:
1. In Admin Center, navigated to **Billing → Licenses**
2. Checked for **Microsoft 365 Business Standard** license
3. Verified the status was **Active** and that sufficient licenses were available (usually 25)

**Why:** Ensuring licenses are available is crucial before creating users; without them, services like Exchange, Teams, and OneDrive will not work.

**Screenshot:**
* `M365_License_Overview.png`

---

## Step 3: Create Cloud Users

### How It Was Done:
1. Navigated to **Users → Active Users**
2. Clicked **Add a user**
3. Entered first name, last name, and username for each user
4. Since the new UI may not show a password section, users were created and passwords were enforced via **Reset Password** later
5. Created multiple users representing different roles (IT, HR, Sales)

**Why:** Users are required for accessing Microsoft 365 services; creating them simulates real company onboarding.

**Screenshot:**
* `M365_Users_Created.png`

---

## Step 4: Assign Microsoft 365 Licenses

### How It Was Done:
1. Selected each newly created user
2. Clicked **Licenses and Apps**
3. Assigned **Microsoft 365 Business Standard license**
4. Saved changes

**Why:** License assignment is mandatory to enable Exchange, Teams, and OneDrive for each user

**Result:** Users now have active mailboxes and access to collaboration services

---

## Step 5: Configure and Test Outlook (Exchange Online)

### How It Was Done:
1. Opened **Outlook Web** at **[https://outlook.office.com](https://outlook.office.com)**
2. Logged in as a test user (e.g., ituser01)
3. Sent a test email to another created user
4. Verified email delivery successfully

**Why:** Testing Outlook ensures that Exchange Online is correctly configured and mailboxes are active

**Screenshot:**
* `Outlook_Email_Test.png`

---

## Step 6: Configure Microsoft Teams

### How It Was Done:
1. Opened Microsoft Teams via **[https://teams.microsoft.com](https://teams.microsoft.com)**
2. Logged in as admin or test user
3. Clicked **Create a Team → From Scratch**
4. Named the team **SECURECORP-IT**
5. Added 2–3 users to the team
6. Sent a test message within the team

**Why:** Teams configuration ensures proper communication and collaboration among users

**Screenshot:**
* `Microsoft_Teams_Configured.png`

---

## Step 7: Configure OneDrive for Business

### How It Was Done:
1. Logged in as a test user at **[https://onedrive.live.com](https://onedrive.live.com)**
2. Uploaded a sample file (e.g., `IT_Security_Policy.docx`)
3. Verified that the file uploaded successfully

**Why:** OneDrive provides cloud storage for users; testing upload confirms storage and sync are working

**Screenshot:**
* `OneDrive_File_Uploaded.png`

---

## Step 8: Access Exchange Admin Center (Admin Verification)

### How It Was Done:
1. From Microsoft 365 Admin Center, navigated to **Show All → Exchange** or directly to **[https://admin.exchange.microsoft.com](https://admin.exchange.microsoft.com)**
2. Logged in with Global Admin credentials when prompted (separate re-authentication is normal for security)
3. Verified left menu loaded (Home, Recipients, Mail flow, Reports, Roles)
4. Clicked **Recipients → Mailboxes**
5. Confirmed that all created users have active mailboxes

**Why:** Accessing Exchange Admin Center shows real administrative exposure and verifies mailbox provisioning

**Screenshot:**
* `Exchange_Admin_Login_Success.png`

---

## Final Outcome of Day 5

* Microsoft 365 Business Standard tenant configured
* Users created and licensed
* Outlook, Teams, and OneDrive verified working
* Exchange Admin Center accessed and user mailboxes confirmed
* Provides professional exposure to cloud administration tasks
...