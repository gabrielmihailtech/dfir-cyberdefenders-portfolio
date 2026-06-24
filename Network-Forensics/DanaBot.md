## 14. DanaBot Lab

### Analysis
A network traffic capture was analyzed using Wireshark to investigate a DanaBot malware infection. The objective was to identify the initial access point,analyze malicious communication,
and extract key indicators of compromise (IOCs). The investigation focused on examining HTTP traffic, identifying suspicious domains, analyzing payload delivery,
and extracting malicious files from network streams.

The analysis involved filtering HTTP traffic, inspecting TCP streams, identifying file downloads, and reviewing server responses. Extracted files were then analyzed to determine their hashes
and execution mechanisms. External threat intelligence platforms were used to validate and enrich the findings.

---

### Findings

- The initial access was traced to a malicious domain resolving to an external IP address:
         IP Address: 62.173.142.148

- Analysis of HTTP traffic revealed the delivery of a malicious file used during initial access:
         File Name: allegato_708.js

- The malicious payload was extracted from the HTTP stream and hashed:
         SHA-256: 847b4ad90b1daba2d9117a8e05776f3f902dda593fb1252289538acf476c4268

- Examination of the HTTP stream revealed the execution mechanism for the malicious payload:
         Process: wscript.exe

- Further analysis identified a secondary payload used by the attacker:
         File Extension: .dll

This indicates the use of dynamic library execution, commonly associated with malware loading techniques.

- The second malicious file was extracted and analyzed:
         File Name: resources.dll
         MD5: e758e07113016aca55d9eda2b0ffeebe

---

### Conclusion
The investigation confirms that the infection chain begins with a malicious HTTP connection to a suspicious domain, delivering an obfuscated JavaScript payload (allegato_708.js). 
The script is executed using wscript.exe, a legitimate Windows scripting engine commonly abused by malware.

Following initial execution, a secondary payload (resources.dll) is downloaded and executed, indicating a multi-stage infection process. This behavior is consistent with DanaBot malware,
which leverages script-based initial access followed by DLL-based payload execution.

The extracted indicators, including IP address, file hashes, and execution processes, provide actionable intelligence for detecting and mitigating similar attacks.
The analysis demonstrates a full attack chain, from initial compromise to payload delivery and execution.
