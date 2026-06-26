## 16. RedLine Lab

### Analysis
This investigation involved memory forensics using Volatility to analyze a compromised system infected with RedLine Stealer malware. The objective was to identify suspicious processes, examine memory artifacts, detect command-and-control (C2) communication, and extract key indicators of compromise (IOCs).

The analysis focused on process enumeration using pstree, detecting injected memory regions with malfind, identifying active and past network connections with netscan, and extracting useful artifacts such as URLs and file paths using the strings utility. The workflow allowed the reconstruction of attacker behavior directly from volatile memory.

---

### Findings

- Analysis of running processes revealed a suspicious executable:
         Suspicious Process: oneetx.exe

- The process tree showed that the suspicious process spawned a child process:
         Child Process: rundll32.exe  

This behavior is commonly associated with malware executing additional payloads using legitimate Windows utilities.

- Memory analysis using malfind identified injected executable regions with the following protection level:
         Memory Protection: PAGE_EXECUTE_READWRITE  

This indicates that the memory region can be read, written, and executed, which is a strong sign of malicious code injection.

- Network analysis revealed a process responsible for VPN tunneling:
         VPN Process: outline.exe  

Further investigation showed that this process utilizes tun2socks, a known tunneling component often used to route traffic through anonymized channels.

- The Command-and-Control (C2) infrastructure was identified:
         Attacker IP Address: 77.91.124.20  

This external IP address represents the communication endpoint used by the malware.

- Strings analysis of the memory dump revealed a full URL accessed by the attacker:
         URL: http://77.91.124.20/store/games/index.php  

This confirms direct interaction with the attacker's infrastructure and potential payload delivery or data exfiltration.

- Further inspection of the process confirmed the full path of the malicious executable:
         File Path:  
        C:\Users\Tammam\AppData\Local\Temp\c3912af058\oneetx.exe  

This location within the Temp directory is commonly abused by malware to evade detection.

---

### Conclusion
The investigation confirms that the system was compromised by RedLine Stealer, a credential-stealing malware commonly used to exfiltrate sensitive data such as browser credentials and system information.

The infection chain shows that a malicious executable (oneetx.exe) was executed from a temporary directory and subsequently launched additional processes (rundll32.exe). The malware performed code injection, as indicated by RWX memory protection, and communicated with a remote attacker-controlled server (77.91.124.20).

Additionally, the use of a VPN tunneling application (outline.exe) highlights efforts to obfuscate network communication and evade detection. The extracted URL further supports the presence of a command-and-control infrastructure used for data exfiltration or payload delivery.

The collected indicators, including process names, file paths, IP addresses, and URLs, are critical for detection, containment, and future threat hunting activities.

---

## 🚨 Key Indicators of Compromise (IOCs)

- Suspicious Process: `oneetx.exe`
- Child Process: `rundll32.exe`
- Memory Protection: `PAGE_EXECUTE_READWRITE`
- VPN Process: `outline.exe`
- Attacker IP: `77.91.124.20`
- Malicious URL: `http://77.91.124.20/store/games/index.php`
- File Path: `C:\Users\Tammam\AppData\Local\Temp\c3912af058\oneetx.exe`

---
``
