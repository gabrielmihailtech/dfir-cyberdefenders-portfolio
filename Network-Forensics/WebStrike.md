1.  WebStrike Lab
 Analysis
Network traffic was analysed using Wireshark to investigate suspicious activity targeting a web server. The analysis focused on HTTP request methods, user-agent strings, file uploads, and outbound connections to identify signs of compromise. Filtering techniques were applied to isolate relevant GET and POST requests, along with HTTP streams, to reconstruct attacker activity.

 Findings
- The attacker originated from Tianjin, identified by extracting the source IP address from HTTP requests and correlating it with geolocation data.
- Analysis of HTTP headers revealed the attacker’s User-Agent:
       Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
- Suspicious HTTP POST requests indicated that a malicious web shell was successfully uploaded:
       Image file: image.jpg.php
- The uploaded file was stored in the following directory:
      /reviews/uploads/
- Examination of HTTP streams revealed outbound communication initiated by the web shell to the attacker’s machine:
      Port: 8080
- Data exfiltration activity was observed through HTTP POST requests, indicating attempts to retrieve sensitive files:
      Targeted file: passwd

Conclusion
The investigation confirms that the web server was compromised through a malicious file upload leading to the deployment of a web shell. The attacker gained remote command execution capabilities, established outbound connections, and attempted data exfiltration. These findings demonstrate a complete web server compromise with active attacker interaction and persistence.
