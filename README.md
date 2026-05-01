# Unauthorized Local Account Investigation - Windows Endpoint

This project simulates a real-world SOC investigation involving the discovery of an unauthorized local account and potential persistence mechanisms on a Windows system.

---

## Scenario

During routine monitoring, unusual after-hours activity was detected on a Windows workstation (FINANCE-PC07). Initial triage revealed the presence of an unknown local user account.

---

## Objective

Determine whether the identified account represents unauthorized persistence or legitimate administrative activity.

---

## Tools Used

- PowerShell  
- Get-LocalUser  
- Get-ChildItem  
- Get-Content  

---

## Investigation Steps

1. Enumerated local user accounts using:
   Get-LocalUser

2. Identified suspicious account:
   shadow-payroll (Enabled)

3. Reviewed user profile directory:
   C:\Users\shadow-payroll

4. Analyzed files within the user directory:
   notes.txt revealed operational instructions indicating suspicious behavior.

---

## Evidence

- Suspicious account name: shadow-payroll  
- Description: "Work hard. Stay hidden."  
- Account is enabled  
- User profile present in system  
- Notes file indicates:
  - VPN usage after working hours
  - Use of administrative shares
  - Log deletion practices  

---

## Indicators of Compromise (IOCs)

- Suspicious local account: shadow-payroll  
- Unusual account description suggesting concealment  
- VPN usage outside normal working hours  
- Use of administrative shares  
- Evidence of log deletion activity  

---

## Analysis

The account naming convention and description strongly suggest intentional concealment.  
The presence of operational notes indicates manual attacker interaction rather than automated system behavior.  
The reference to VPN access and administrative shares suggests potential lateral movement or unauthorized access.  
The mention of log deletion is a strong indicator of an attempt to evade detection.

---

## Conclusion

This activity is highly suspicious and likely represents unauthorized access with persistence mechanisms established on the system.

---

## Risk Assessment

Severity: HIGH

---

## Detection Opportunity

This activity could have been detected earlier through:

- Monitoring newly created local accounts  
- Alerting on after-hours VPN access  
- Detection of unusual administrative share usage  
- Monitoring log deletion activity  

Implementing these controls could improve early detection and response capabilities.

---

## Recommended Actions

- Disable the suspicious account immediately  
- Preserve and collect system logs before further deletion  
- Investigate lateral movement across the network  
- Perform full endpoint forensic analysis  
- Reset credentials for affected systems  

---

## Skills Demonstrated

- Windows endpoint triage  
- User account investigation  
- File system analysis  
- Threat identification  
- Incident response fundamentals  
- Analytical thinking in security scenarios  
