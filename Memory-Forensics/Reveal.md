17. Reveal Lab

Analysis
This investigation focused on reconstructing a multi-stage attack using memory forensics techniques with Volatility 3. The primary objective was to identify malicious processes, analyze process hierarchies, extract command-line artifacts, and correlate the findings with threat intelligence sources to determine the malware family involved.
The analysis began with process enumeration using pstree to identify abnormal execution patterns, followed by examination of parent-child relationships to understand how the attack was initiated. Additional investigation included identifying second-stage payload execution, extracting network artifacts using strings, and mapping observed tactics to MITRE ATT&CK techniques. Finally, external threat intelligence platforms were used to correlate indicators of compromise (IOCs) with known malware families.

Findings
- Process analysis revealed a suspicious process commonly used in fileless attacks:
        Malicious Process: powershell.exe
- The process hierarchy helped identify how the malicious process was executed:
         Parent PID: 4120  
This indicates that the malicious PowerShell process was launched from another legitimate process, suggesting possible user execution or scripted activity.
- Further inspection uncovered the file used for second-stage payload execution:
         Payload File: 3435.dll  
This demonstrates the use of a DLL-based payload for executing malicious code.
- Network-related artifact extraction identified a shared directory on a remote server:
         Shared Directory: davwwwroot  
This indicates that the attacker accessed or interacted with a WebDAV resource on the remote host.
- The execution technique used by the attacker was mapped to MITRE ATT&CK:
         Technique: T1218.011 (Rundll32)  
This confirms the use of a Windows binary (rundll32.exe) to execute the malicious DLL payload, a common defense evasion technique.
- Analysis of security identifiers (SIDs) revealed the compromised user account:
        Username: Elon  
This indicates the malware was executed under a user-level account rather than a system-level context.
- Correlation with threat intelligence platforms using the identified IP address led to the attribution of the malware family:
         Malware Family: STRELASTEALER  
This matches known behaviors associated with information-stealing malware used to exfiltrate user data.

Conclusion
The analysis confirms a multi-stage attack leveraging PowerShell execution followed by DLL-based payload delivery. The attacker utilized built-in Windows utilities such as rundll32.exe to execute malicious code, effectively blending in with legitimate system activity and evading detection.
The presence of a WebDAV directory (davwwwroot) indicates interaction with a remote server, potentially for payload delivery or data exfiltration. Running under a legitimate user account (Elon) further demonstrates the attacker’s reliance on user-level execution to maintain stealth.
Correlation with external threat intelligence identified the malware as StrelaStealer, a known information-stealing malware family. This aligns with observed behaviors such as staged execution, use of legitimate binaries, and communication with external infrastructure.
The findings highlight the importance of monitoring process hierarchies, detecting abuse of legitimate Windows binaries, and correlating memory artifacts with threat intelligence to fully understand and respond to attacks.

🚨 Key Indicators of Compromise (IOCs)
- Malicious Process: `powershell.exe`
- Parent PID: `4120`
- Payload File: `3435.dll`
- Shared Directory: `davwwwroot`
- MITRE Technique: `T1218.011`
- Username: `Elon`
- Malware Family: `STRELASTEALER`
