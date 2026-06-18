5.Amadey APT (C-36) Lab
Analysis
Memory forensics analysis was performed using Volatility 3 on a Windows 7 memory dump to identify malicious processes, network activity, and persistence mechanisms. Several plugins were used, including process tree inspection, command-line analysis, network scanning, and file artifact discovery. The investigation focused on identifying the root process of the infection, command-and-control (C2) communication, payload delivery, and execution flow.

Findings
- Process tree analysis revealed a suspicious process masquerading as a legitimate system process:
          Malicious parent process: lssass.exe
- Command-line analysis identified the execution location of the malware:
          C:\Users\0XSH3R~1\AppData\Local\Temp\925e7e99c5\lssass.exe
- Network analysis exposed active communication with a command-and-control server:
          C2 server IP: 41.75.84.12
- Memory analysis of the process confirmed attempts to retrieve additional payloads:
          Number of files requested: 2
- Further investigation revealed the downloaded malicious component:
          C:\Users\0xSh3rl0ck\AppData\Roaming\116711e5a2ab05\clip64.dll
- Process tree inspection showed how the payload was executed:
          Child process: rundll32.exe
- File system artifact scanning identified persistence mechanisms:
          Scheduled task location: C:\Windows\System32\Tasks\lssass.exe

Conclusion
The analysis confirms that the system was compromised by the Amadey trojan, which used a disguised process to evade detection. The malware established communication with a remote C2 server, downloaded additional malicious components, and executed them using rundll32.exe. Persistence was achieved through scheduled tasks, ensuring continued execution after system reboot. These behaviors demonstrate a full compromise involving payload delivery, execution, and long-term persistence.

