3. Poisoned Credentials Lab
 Analysis
Network traffic was analyzed using Wireshark to investigate a suspected LLMNR/NBT-NS poisoning attack. The analysis focused on name resolution traffic, rogue responses, and NTLM authentication exchanges. Filtering techniques were applied to identify unusual queries, poisoned responses, and credential exposure during SMB authentication.

Findings
- Analysis of LLMNR traffic revealed a mistyped query issued by a legitimate host: 
            Query: fileshaare
            Source IP: 192.168.232.162
- A rogue machine was identified responding to this query with spoofed information:
            Rogue IP address: 192.168.232.215
- Further investigation identified additional compromised hosts receiving poisoned responses:
           Second affected machine: 192.168.232.176
- NTLM authentication traffic was analyzed to identify compromised credentials:
           Username: janesmith
- Examination of SMB Session Setup responses revealed the target system accessed by the attacker:
           Hostname: AccountPC

Conclusion
The investigation confirmed a successful LLMNR/NBT-NS poisoning attack, where the attacker exploited a mistyped network request to impersonate a legitimate service. This allowed the rogue system to capture authentication attempts and compromise user credentials. The attacker then used the stolen credentials to access additional systems via SMB, demonstrating lateral movement within the network.
