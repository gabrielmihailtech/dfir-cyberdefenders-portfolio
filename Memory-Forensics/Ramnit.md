## Ramnit Malware Analysis (Memory Forensics)

### 🔎 Lab Summary
This investigation focused on analyzing a Windows memory dump using Volatility 3 to identify a malicious process, extract network indicators of compromise (IOCs), recover the malware executable, and correlate findings with external threat intelligence sources.

---

## 🧰 Tools Used
- Volatility 3
- VirusTotal
- ipinfo.io

---

## 🎯 Objectives
- Identify the suspicious process in memory
- Determine execution path of the malware
- Extract network communication artifacts
- Recover and hash the malicious binary
- Identify compilation metadata
- Correlate findings with external threat intelligence

---

## 🔍 Findings

### 1. Malicious Process Identification
Using memory analysis, the suspicious process was identified:

- **Process Name:** `ChromeSetup.exe`

This process mimics a legitimate installer to evade detection.

---

### 2. Executable Path
The full path of the malicious executable was recovered:

- **Path:**  
  `C:\Users\alex\Downloads\ChromeSetup.exe`

This indicates execution from a user-accessible location, a common tactic used by malware.

---

### 3. Network Communication (IOC)
Network analysis revealed an external IP address contacted by the malware:

- **IP Address:** `58.64.204.181`

This indicates command-and-control (C2) or payload retrieval activity.

---

### 4. Geolocation of IP
The IP address was analyzed using external threat intelligence:

- **Location:** Hong Kong

This helps contextualize the origin of the malicious infrastructure.

---

### 5. File Hash (SHA1)
The malware binary was extracted from memory and hashed:

- **SHA1 Hash:**  
  `280c9d36039f9432433893dee6126d72b9112ad2`

This allows for identification and cross-system detection.

---

### 6. Compilation Timestamp
The malware’s build time was extracted:

- **Compilation Time:**  
  `2019-12-01 08:36`

This provides insight into the malware development timeline.

---

### 7. Associated Domain
Through VirusTotal correlation:

- **Domain:** `dnsnb8.net`

This domain is associated with malicious activity and should be blocked.

---

## 🧠 Conclusion

The analysis confirmed that the system was infected with a Ramnit-like malware variant disguised as a Chrome installer. The malware executed from a user directory, established outbound communication with a remote server in Hong Kong, and utilized external domains for malicious operations.

Key indicators such as the process name, file hash, IP address, and domain provide actionable threat intelligence for detection, blocking, and prevention.

---

## 🚨 Key Indicators of Compromise (IOCs)

- Process: `ChromeSetup.exe`
- Path: `C:\Users\alex\Downloads\ChromeSetup.exe`
- IP: `58.64.204.181`
- Domain: `dnsnb8.net`
- SHA1: `280c9d36039f9432433893dee6126d72b9112ad2`

---
