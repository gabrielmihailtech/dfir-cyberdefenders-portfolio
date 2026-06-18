8. JetBrains Lab
Analysis
Network traffic was analyzed using Wireshark to investigate a suspected web server compromise targeting a JetBrains TeamCity instance. The analysis focused on HTTP requests, server responses, file uploads, and command execution patterns. Particular attention was given to identifying attacker activity, exploited vulnerabilities, credential creation, and persistence mechanisms.
Filtering techniques were applied to isolate attacker interactions, including POST requests, HTTP streams, and specific URIs related to TeamCity REST API endpoints.

 Findings
- Analysis of HTTP POST requests identified the attacker’s source IP address:
         Attacker IP: 23.158.56.196
- Investigation of server responses revealed the version of the affected web service:
         Service version: 2023.11.3
- Correlation of the service version with public vulnerability databases identified the exploited vulnerability:
         CVE: CVE-2024-27198
- Examination of HTTP request payloads showed that the attacker created a new user account:
         Credentials: c91oyemw:CL5vzdwLuK
- File upload activity was identified through HTTP POST requests to the plugin upload endpoint:
         Uploaded web shell file: NSt8bHTg.zip

- Analysis of subsequent HTTP activity revealed command execution via the uploaded web shell:
       First command execution timestamp: 2024-06-30 08:03

Conclusion
The investigation confirms that the attacker successfully exploited a vulnerable JetBrains TeamCity instance using CVE-2024-27198. The attacker established persistence by creating a new user account and uploading a malicious web shell. This allowed remote command execution and ongoing control of the system. The attack demonstrates a full compromise chain, including initial access, exploitation, persistence, and execution, highlighting the risks of unpatched web services.
