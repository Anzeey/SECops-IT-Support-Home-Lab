# DAY 3 — Active Directory Users, Groups & Organizational Units

**Project:** SecureCorp IT Support Lab  
**Domain:** SecureCorp.local  
**Server:** Windows Server 2022 (Domain Controller)  
**Client:** Windows 10/11 (Domain Joined)

---

## 1. Objective

The objective of Day 3 was to design and implement a proper Active Directory structure for SecureCorp by:

- Creating a logical Organizational Unit (OU) hierarchy
- Creating 25–30 domain user accounts
- Creating security groups and assigning users
- Testing domain login from a client machine

This setup simulates a real enterprise (MNC-style) Active Directory environment.

---

## 2. Tools Used

- Windows Server 2022  
- Active Directory Users and Computers (ADUC)  
- Windows 10/11 Client VM  
- Command Prompt (`whoami` verification)

---

## 3. Active Directory OU Structure

A structured OU hierarchy was created to organize users department-wise while keeping default system containers unchanged.

### OU Hierarchy Implemented

SecureCorp.local
├── Builtin
├── Computers
├── Domain Controllers
├── ForeignSecurityPrincipals
├── Managed Service Accounts
├── Users
│ ├── Hassan Mirza
│ ├── Helena Silva
│ ├── Marco Conti
│ ├── Qureshi Abraham
│ └── Zayed Masood
├── IT
│ ├── Anna Muller
│ ├── Erik Johansson
│ ├── Lukas Schneider
│ ├── Matteo Rossi
│ └── Sofia Novak
├── HR
│ ├── Clara Dubois
│ ├── Daniel Horvath
│ ├── Elena Petrova
│ ├── Hugo Martin
│ └── Marta Kowalska
├── Finance
│ ├── Isabel Garcia
│ ├── Ivana Dimitrova
│ ├── Piotr Zielinski
│ ├── Sana Khalid
│ └── Thomas Fischer
├── Sales
│ ├── Emil Hansen
│ ├── Hamza Rehman
│ ├── Laura Schmidt
│ ├── Niha Fatima
│ └── Noor Fatima
├── Interns
│ ├── Hassan Mirza
│ ├── Helena Silva
│ ├── Marco Conti
│ ├── Qureshi Abraham
│ └── Zayed Masood
├── Management
│ ├── Francois Bernard
│ ├── Henrik Olsen
│ ├── Katarina Svensson
│ ├── Khalid Mahmood
│ └── Samina Ahmed
└── Groups
├── Finance Team
├── HR Team
├── Interns Team
├── IT Admins
├── Management Team
└── Sales Team


### Screenshot Evidence
- **Screenshot Name:** `OU_Structure.png`  
- **Description:** Displays the OU hierarchy inside Active Directory Users and Computers.

---

## 4. User Account Creation

A total of 30 domain user accounts were created and placed into their respective departmental OUs.

### User Distribution

- IT: 5 users  
- HR: 5 users  
- Finance: 5 users  
- Sales: 5 users  
- Interns: 5 users  
- Management: 5 users  

Each user account was configured with:
- Proper full name
- Domain login credentials
- Standard password configuration (test environment)

---

## 5. Security Groups Configuration

A dedicated **Groups** OU was created to manage security groups following enterprise best practices.

### Security Groups Created

| Group Name | Purpose |
|----------|--------|
| IT Admins | IT department administrative users |
| HR Team | HR department users |
| Finance Team | Finance department users |
| Sales Team | Sales department users |
| Interns Team | Intern users |
| Management Team | Management-level users |

### Group Type and Scope

- **Group Type:** Security  
- **Group Scope:** Global  

### Membership Assignment

Users from each department were added to their corresponding security groups.  
Example:
- IT users → IT Admins  
- HR users → HR Team  

---

### Screenshot Evidence
- **Screenshot Name:** `ADUC_Open.png`  
- **Description:** Active Directory Users and Computers console showing the Groups OU and security groups.

---

## 6. Domain Login Testing (Client Verification)

Domain login was tested from a Windows 10/11 client machine to verify Active Directory functionality.

### Steps Performed

1. Client machine was logged out.
2. Login was attempted using a domain user account.
3. Successful desktop access was confirmed.
4. Command Prompt was used to verify the logged-in identity.

### Verification Command

```cmd
whoami

SecureCorp\anna.Muller

| Screenshot Name  | Description                            |
| ---------------- | -------------------------------------- |
| ClientLogin.png  | Successful domain user login on client |
| ClientWhoami.png | whoami command confirming domain user  |


## 8. Outcome

By the end of Day 3:

- A professional Active Directory structure was successfully implemented.
- Users and security groups were organized according to enterprise (MNC) standards.
- Successful domain authentication was verified through client-side login testing.

This completes **Day 3 — Active Directory Users, Groups & Organizational Units**.




