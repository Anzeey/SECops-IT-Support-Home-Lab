# DAY 8 — Intune Testing & Reporting

## Objective
The objective of Day 8 was to validate Microsoft Intune security enforcement, test device compliance behavior, verify Conditional Access restrictions, and generate administrative reports for compliance and application deployment. This phase focuses on **real-world endpoint security testing and enterprise-grade reporting**.

---

## Environment Overview
- **Platform:** Microsoft Endpoint Manager (Intune)
- **Device Type:** Windows 10 / Windows 11 (Azure AD joined)
- **MDM Authority:** Microsoft Intune
- **Applications Deployed:** Microsoft Teams, Google Chrome
- **Security Controls:** Compliance Policies, Conditional Access

---

## 1. Simulate Non-Compliant Device

### Purpose
To verify how Intune detects and flags devices that fail to meet organizational compliance policies.

### Action Performed
- Modified device compliance policy settings.
- Triggered device sync with Intune.
- Allowed Intune to re-evaluate device compliance.

### Expected Result
- Device marked as **Non-Compliant**
- Compliance failure reason visible in Intune

### Evidence Captured
- `SS_Compliance_Settings.png` – Compliance policy configuration  
- `Non-Compliant.png` – Device showing non-compliant status  
- `Compliance-failure.png` – Compliance failure details  
- `Non_Compliant_Device.png` – Highlighted test device  

---

## 2. Verify Conditional Access Restriction

### Purpose
To ensure non-compliant devices are blocked from accessing corporate resources.

### Action Performed
- Configured Conditional Access policy requiring device compliance.
- Applied policy to users and cloud applications.
- Attempted sign-in from a non-compliant device.

### Expected Result
- Access denied for non-compliant device
- User receives compliance-related error message

### Evidence Captured
- `Conditional-access-configured.png` – Conditional Access policy configuration  
- `Conditional Access-Access Denied.png` – Access blocked due to non-compliance  

---

## 3. Perform Remote Device Lock

### Purpose
To remotely lock a device in the event of theft, loss, or security risk.

### Process (No Screenshots)
1. Navigate to **Endpoint Manager → Devices → All devices**
2. Select the target device
3. Choose **Remote lock**
4. Confirm the action

### Important Note
> ⚠️ Remote Device Lock is **not supported on all operating systems or device types**.  
> Support depends on OS version, enrollment method, and manufacturer limitations.

---

## 4. Perform Remote Device Wipe

### Purpose
To remove corporate data and reset a device during incidents or device decommissioning.

### Process (No Screenshots)
1. Navigate to **Endpoint Manager → Devices → All devices**
2. Select the test device
3. Choose **Wipe**
4. Confirm wipe options
5. Device resets and is removed from Intune

### Common Use Cases
- Employee offboarding  
- Compromised devices  
- Lost or stolen endpoints  

---

## 5. Generate Device Compliance Report

### Purpose
To generate an administrative report displaying compliance status across all managed devices.

### Action Performed
- Navigated to Intune reporting section
- Viewed device compliance summary
- Exported compliance report

### Report Includes
- Device name
- Assigned user
- Compliance status
- Last check-in time
- Non-compliance reason

### Evidence Captured
- `Device_Compliance_Summary.png` – Compliance overview dashboard  
- `Compliance_Report_Export.png` – Export confirmation  
- `Compliance_Report_Details.png` – Detailed compliance report  
- `Non_Compliant_Device.png` – Non-compliant device highlighted  

---

## 6. Generate App Deployment Report

### Purpose
To verify successful deployment of applications pushed via Intune.

### Action Performed
- Navigated to **Apps → Monitor → App install status**
- Selected deployed applications
- Reviewed installation results
- Exported app deployment report

### Report Includes
- Application name
- Device name
- Installation status (Installed / Failed / Pending)
- Deployment timestamp

### Evidence Captured
- `App Install Status.png` – App deployment overview  
- `App_Deployment_Export.png` – Exported deployment report  
- `App_Deployment_Details.png` – Detailed installation status  

---

## Final Outcome
- ✅ Non-compliant devices correctly identified
- ✅ Conditional Access enforced successfully
- ✅ Compliance and app deployment reports generated
- ✅ Enterprise-grade documentation completed

---

## Skills Demonstrated
- Microsoft Intune Administration  
- Endpoint Security & Compliance  
- Conditional Access Configuration  
- Application Deployment Monitoring  
- Professional IT Documentation  
