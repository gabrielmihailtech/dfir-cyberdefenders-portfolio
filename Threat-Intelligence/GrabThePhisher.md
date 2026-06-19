11.GrabThePhisher Lab
Analysis
A phishing kit targeting cryptocurrency users was analyzed to identify credential harvesting techniques, exfiltration mechanisms, and threat actor infrastructure. The analysis focused on examining web files, backend PHP scripts, and locally stored logs to extract indicators of compromise (IOCs) and attacker information.
The investigation included reviewing HTML content, inspecting PHP code responsible for handling user data, and analyzing log files containing stolen information.

Findings
- Analysis of the phishing page revealed the targeted cryptocurrency wallet:
        Wallet: MetaMask

- The main backend file responsible for handling phishing operations was identified:
        File name: metamask.php
        Language: PHP

- The phishing kit collects victim system information using an external geolocation service:
        Service used: sypex geo

- Examination of local log files revealed previously harvested credentials:
         Number of collected seed phrases: 3

- The most recent compromised seed phrase was identified:
         Seed phrase: father also recycle embody balance concert mechanic believe owner pair muffin hockey

- Analysis of the exfiltration mechanism revealed that captured data is sent to an external communication platform:
         Medium: Telegram

- Credentials for accessing the attacker’s Telegram bot were extracted:
         Bot token: 5457463144:AAG8t4k7e2ew3tTi0IBShcWbSia0Irvxm10

- Communication channel details were identified:
          Chat ID: 5442785564

- Hidden comments in the PHP file revealed attacker attribution information:
          Developer alias: j1j1b1s@m3r0

Conclusion
The investigation confirms that the phishing kit is designed to target MetaMask users by harvesting wallet seed phrases and exfiltrating them via a Telegram bot. The kit collects additional victim information, including IP address and geolocation data, using an external API (SypexGeo). Analysis of local logs demonstrated successful data capture, while embedded developer comments provided valuable threat actor attribution. The attack demonstrates a complete phishing workflow, from credential harvesting to automated exfiltration and attacker identification.
