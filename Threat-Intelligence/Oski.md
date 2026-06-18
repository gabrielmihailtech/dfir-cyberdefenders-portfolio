2. Oski Lab

Analysis
The malware sample was analyzed using a combination of VirusTotal and the Any.Run sandbox environment. The investigation focused on identifying behavioral indicators, communication patterns, and configuration data associated with the malware. Particular attention was given to command-and-control (C2) communication, credential theft techniques, and post-execution cleanup mechanisms.

Findings
- Malware creation metadata obtained from VirusTotal indicated:
       Creation time: 2022-09-28 17:40
- Command-and-control (C2) communication was identified through network indicators:
       http://171.22.28.221/5c06c05b7b34e8e6.php
- Post-infection behavior showed that the malware loaded external libraries to support its functionality:
       First requested library: sqlite3.dll
- Configuration analysis from the Any.Run sandbox revealed encryption parameters:
      RC4 key used for string decryption: 5329514621441247975720749009
- MITRE ATT&CK mapping identified the primary credential theft technique:
       T1555 – Credentials from Password Stores
- Analysis of child processes indicated cleanup and anti-forensic behavior:
       Target directory for DLL deletion: C:\ProgramData
- Post-exfiltration behavior demonstrated evasion mechanisms:
        Malware self-deletes after: 5 seconds

Conclusion
The Oski malware exhibits typical information-stealer behavior, including credential harvesting, encrypted configuration usage, and communication with a remote C2 server. The malware leverages system libraries and command-line execution to operate and subsequently remove traces of its activity. Its alignment with MITRE ATT&CK technique T1555 highlights its focus on extracting credentials from local storage, indicating a high-risk data exfiltration threat.
