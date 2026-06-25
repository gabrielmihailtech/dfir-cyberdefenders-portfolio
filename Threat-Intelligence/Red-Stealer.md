## 15. Red Stealer Lab

### Analysis
This investigation focused on analyzing a suspicious executable using threat intelligence platforms such as VirusTotal and MalwareBazaar. The objective was to identify the malware classification, extract key indicators of compromise (IOCs), understand its behavior, and correlate its actions with MITRE ATT&CK techniques.

The analysis involved examining detection results, reviewing file metadata, analyzing network communication, identifying DNS activity, and inspecting imported DLLs used for privilege escalation. Additional correlation was performed using ThreatFox to associate the malware with known threat intelligence data and aliases.

---

### Findings

- VirusTotal classification identified the malware category:
         Category: Trojan

- The file name associated with the malicious sample was:
         File Name: Wextract

- The first submission timestamp provides insight into when the malware was initially observed:
         First Seen: 2023-10-06 04:41 UTC

- Analysis of the malware behavior mapped its data collection activity to a MITRE ATT&CK technique:
         Technique ID: T1005 (Data from Local System)

- Network analysis revealed DNS queries to social media-related infrastructure:
         Domain: facebook.com

- The malware communicated with an external IP address and port:
         IP Address: 77.91.124.55  
         Port: 19071

- Using MalwareBazaar and external OSINT, the YARA rule created by Varp0s was identified:
         YARA Rule: detect_Redline_Stealer

- ThreatFox correlation revealed an alias associated with the malicious infrastructure:
         Malware Alias: RECORDSTEALER

- Analysis of imported DLL functions identified the library used for privilege escalation:
         DLL: advapi32.dll

---

### Conclusion
The investigation confirms that the analyzed sample is a Trojan associated with the RedLine Stealer malware family. The malware leverages social engineering and execution mechanisms to infect the system, followed by data collection from local sources such as browser storage and user credentials.

It communicates with external infrastructure, including specific IP addresses and legitimate services, to maintain control and exfiltrate collected data. The use of MITRE ATT&CK technique T1005 highlights its capability to gather sensitive information prior to exfiltration.

The malware also employs privilege escalation techniques through the use of Windows security APIs (advapi32.dll) and demonstrates defense evasion tactics by leveraging legitimate system components. The identification of associated YARA rules and aliases through MalwareBazaar and ThreatFox further enriches the intelligence, enabling improved detection and response capabilities.

---

## 🚨 Key Indicators of Compromise (IOCs)

- File: `Wextract`
- Category: Trojan
- First Seen: `2023-10-06 04:41 UTC`
- MITRE Technique: `T1005`
- Domain: `facebook.com`
- IP: `77.91.124.55:19071`
- YARA Rule: `detect_Redline_Stealer`
- Alias: `RECORDSTEALER`
- DLL: `advapi32.dll`

---
