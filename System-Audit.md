 

## Section 1 – System Information

### Operating System
- OS Name: Windows 11  
- Edition: Windows 11 Pro  
- Version: 23H2 (OS Build 22631.1194)

### Hardware Specifications
- Processor: 11th Gen Intel(R) Core(TM) i3-1115G4 @ 3.00GHz  
- Installed RAM: 8 GB  
- Storage Capacity: 238 GB  
- Storage Type: SSD  
- System Type: 64-bit Operating System  

---

## Section 2 – Access Control Model

Windows 11 primarily uses the Discretionary Access Control (DAC) model. In DAC, the owner of a resource determines who has access to it and what permissions they are granted.

According to NIST (National Institute of Standards and Technology):

“Discretionary Access Control (DAC) is an access control policy determined by the owner of an object. The owner decides which subjects are allowed to access the object and what privileges they have.”
(Source: NIST SP 800-12)

### Principle of Least Privilege (PoLP) Example

On my Windows 11 system, critical processes such as MsMpEng.exe (Microsoft Defender Antivirus) run under the SYSTEM account, while applications like explorer.exe run under my standard user account. I cannot terminate or modify SYSTEM-level processes without administrative privileges.

This demonstrates the Principle of Least Privilege because Windows restricts users to the minimum permissions necessary to perform their tasks. Elevated privileges require administrator authentication through User Account Control (UAC), which reduces the risk of unauthorized system changes.

---

## Section 3 – Process Analysis

### 1. Process Name: MsMpEng.exe  
- PID: 9536  
- Description: MsMpEng.exe is the Microsoft Defender Antivirus service responsible for real-time malware detection and system protection.  
- Security Risk Hypothesis: If an attacker gains SYSTEM-level access through exploitation of this process, they could disable antivirus protection, allowing malware persistence, privilege escalation, and lateral movement across the system.

---

### 2. Process Name: explorer.exe  
- PID: 17434  
- Description: Explorer.exe manages the Windows graphical user interface, including the desktop, taskbar, and file management system.  
- Security Risk Hypothesis: If compromised, an attacker could inject malicious code into the user session, manipulate files, steal sensitive data, or execute unauthorized payloads without raising immediate suspicion.

---

### 3. Process Name: dllhost.exe (COM Surrogate)  
- PID: 33544  
- Description: dllhost.exe hosts COM objects and allows Windows to safely run certain extensions and system components separately from main processes.  
- Security Risk Hypothesis: Attackers may disguise malware as dllhost.exe to evade detection. If exploited, it could be used for stealthy persistence, fileless malware execution, or privilege escalation within the operating system.
