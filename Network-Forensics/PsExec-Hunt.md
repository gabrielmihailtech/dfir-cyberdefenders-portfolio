9. PsExec Hunt Lab
Analysis
Network traffic was analyzed using Wireshark to investigate lateral movement activity within the network. The analysis focused on SMB and SMB2 traffic to identify authentication events, file transfers, and administrative service execution. Special attention was given to NTLM authentication exchanges, SMB tree connections, and process-related artifacts associated with PsExec activity.
Filtering techniques were applied to isolate relevant SMB commands, NTLMSSP authentication messages, and service creation behavior.

Findings
- Initial access was traced by analyzing SMB session setup requests:
        Source IP (attacker entry point): 10.0.0.130
- NTLM authentication challenge responses revealed the first pivot target system:
        Hostname: SALES-PC
- Credential analysis identified the compromised account used by the attacker:
        Username: ssales
- SMB file operations revealed the deployment of a service executable:
        Service file: PSEXESVC.exe

- Analysis of SMB tree connections identified the administrative share used to deploy the service:
        Share used for installation: ADMIN$
- Further investigation revealed the communication channel used between systems:
        Communication share: IPC$
- Continued SMB activity indicated additional lateral movement:
        Second pivot target hostname: MARKETING-PC

Conclusion
The investigation confirms that the attacker used PsExec to perform lateral movement within the network. After gaining initial access, the attacker authenticated using compromised credentials and deployed a malicious service (PSEXESVC.exe) via the ADMIN$ share. Communication between systems was maintained through the IPC$ share. The attacker then expanded access by pivoting to additional hosts, demonstrating a structured lateral movement technique commonly used in Windows environments.
