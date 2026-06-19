4. Yellow RAT Lab

Analysis
Threat intelligence analysis was conducted using VirusTotal and Red Canary resources to investigate a malware sample associated with suspicious network activity. The analysis focused on identifying indicators of compromise (IOCs), command-and-control (C2) communication, file artifacts, and malware behavior patterns.

 Findings
- Malware classification based on VirusTotal detections identified the family as:
  - Yellow Cockatoo RAT
- Examination of file metadata revealed commonly used filenames:
  -111bc461-1ca8-43c6-97ed-911e0e69fdf8.dll
- Portable Executable (PE) analysis provided insight into the malware’s development timeline:
  -Compilation timestamp: 2020-09-24 18:26
- VirusTotal submission data indicated when the malware was first observed:
  -First submission: 2020-10-15 02:47
- Threat intelligence research identified additional dropped artifacts:
  -solarmarker.dat 
- Network behavior analysis revealed communication with a remote command-and-control server:
  -https://gogohid.com

Conclusion
The analyzed malware belongs to the Yellow Cockatoo family, a known remote access trojan (RAT) associated with data exfiltration and persistent access. The malware leverages DLL execution, drops additional components in user directories, and communicates with external C2 infrastructure. These behaviors indicate a structured post-compromise framework designed for data theft and long-term persistence within infected systems.
