## 18. 3CX Supply Chain Lab

### Analysis
This investigation focused on reconstructing the 3CX supply chain attack by analyzing publicly available threat intelligence reports, MSI installer artifacts, malicious DLLs, and malware behavior. The objective was to identify compromised software versions, extract malicious components, understand attacker techniques, map activities to MITRE ATT&CK, and attribute the campaign to a known threat actor.

The analysis combined static analysis techniques, threat intelligence research, MITRE ATT&CK mapping, and behavioral analysis using VirusTotal. Examination of the compromised MSI installer revealed malicious DLLs used during the attack, while additional threat intelligence sources helped identify anti-analysis techniques, encryption methods, and attribution linked to the campaign.

---

### Findings

- Threat intelligence reports identified the number of compromised 3CX Windows versions:
        ➜ Compromised Versions: 2

- Metadata analysis of the malicious MSI installer revealed its creation timestamp:
        ➜ Creation Time (UTC): 2023-03-13 06:33

- Static analysis of the MSI package identified two malicious DLLs dropped during installation:
        ➜ ffmpeg.dll
        ➜ d3dcompiler_47.dll

- Investigation of the DLL loading mechanism mapped the attack technique to MITRE ATT&CK:
        ➜ MITRE Technique: T1574 (Hijack Execution Flow)

- Analysis of VirusTotal detection results categorized the malicious DLLs as:
        ➜ Category: Trojan

- Behavioral analysis identified virtualization and sandbox evasion techniques:
        ➜ MITRE Technique: T1497 (Virtualization/Sandbox Evasion)

- Examination of anti-analysis functionality showed that the malware specifically targeted:
        ➜ Hypervisor: VMware

- Cryptographic analysis revealed the algorithm used by the malware:
        ➜ Encryption Algorithm: RC4

- Threat intelligence correlation attributed the campaign to a known threat actor:
        ➜ Threat Actor: Lazarus Group

---

### Conclusion
The investigation confirms that the 3CX incident was a sophisticated supply chain compromise involving trojanized software distributed through legitimate update mechanisms. The attackers embedded malicious DLLs within the MSI installation package and leveraged DLL hijacking techniques to execute malicious code while appearing as legitimate application components.

The malware incorporated several defense evasion mechanisms, including virtualization and sandbox detection targeting VMware environments. In addition, the use of RC4 encryption helped conceal malicious activity and payload execution.

Threat intelligence reporting from multiple security vendors linked the operation to the Lazarus Group, a threat actor known for conducting large-scale supply chain attacks and financially motivated campaigns. The combination of DLL hijacking, anti-analysis techniques, encrypted communication, and trusted software distribution demonstrates a highly sophisticated intrusion strategy.

The findings highlight the importance of software supply chain security, application integrity verification, behavioral monitoring, and threat intelligence correlation to identify and mitigate advanced threats.

---

## 🚨 Key Indicators and Findings

- Compromised Versions: `2`
- MSI Creation Time (UTC): `2023-03-13 06:33`
- Malicious DLLs:
  - `ffmpeg.dll`
  - `d3dcompiler_47.dll`
- MITRE Technique: `T1574`
- Threat Category: `Trojan`
- Sandbox Evasion Technique: `T1497`
- Targeted Hypervisor: `VMware`
- Encryption Algorithm: `RC4`
- Threat Actor: `Lazarus Group`

---
