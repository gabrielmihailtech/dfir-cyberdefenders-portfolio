## IcedID Lab

### Analysis
The investigation focused on analyzing an IcedID malware sample using VirusTotal and external threat intelligence platforms.
The analysis aimed to identify the malware’s associated artifacts, network behavior, infrastructure, and linked threat actors.

The workflow included examining file metadata, dropped artifacts, contacted domains, and external intelligence sources such as MITRE ATT&CK and sandbox analysis platforms.

---

### Findings
- The initial analysis of the provided hash revealed the primary file used in the infection:
  - File name: document-1982481273.xlsm

- Examination of dropped files identified an additional payload delivered by the malware:
  - Dropped file: 3003.gif

- Network analysis showed that the malware contacted multiple domains to retrieve additional payloads:
  - Number of domains contacted: 5

- Further investigation into the infrastructure revealed the predominant domain registrar used by the threat actor:
  - Registrar: NameCheap

- Threat intelligence correlation using MITRE ATT&CK linked the malware to a known threat group:
  - Threat actor: GOLD CABIN

- Analysis of the execution phase revealed the function used to retrieve additional payloads from remote sources:
  - Function: URLDownloadToFileA

---

### Conclusion
The investigation confirmed that the sample belongs to the IcedID malware family, which is associated with the threat actor GOLD CABIN.
The malware leverages macro-enabled documents for initial delivery, retrieves additional payloads through network communication with attacker-controlled domains,
and uses specific Windows API functions for downloading further components. The use of a consistent registrar infrastructure and identifiable artifacts highlights
patterns that can be used for detection and threat hunting.
