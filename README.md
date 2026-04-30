# eJPT Journey — No Shortcuts

This repository documents my **hands-on preparation for the eLearnSecurity Junior Penetration Tester (eJPT)** certification.

Everything here reflects **real lab work, manual enumeration, and practical penetration testing methodology** — no shortcuts, no copy-paste walkthroughs.

---

# 🎯 Objective

## 🚀 What This Repository Shows

This repository demonstrates my ability to:

- Perform full-service enumeration on target systems  
- Identify misconfigurations and exposed services  
- Analyze real vulnerabilities in lab environments  
- Navigate Linux systems and restricted shells  
- Document findings in a structured, professional format    


# 🧪 Lab Environment

**Attacker Machine:** Kali Linux  
**Target Machine:** Metasploitable 2  
**Platform:** VMware Workstation  

All testing is performed in a **controlled and isolated lab environment**.

---

# 🔥 Highlighted Work

## 🧪 Pickle Rick (TryHackMe)
- Discovered hidden credentials via **page source inspection**
- Extracted sensitive data from **robots.txt**
- Performed **directory enumeration** to uncover hidden endpoints
- Gained access to a **web-based command execution interface**
- Navigated system directories to retrieve sensitive files under restricted conditions

---

## 🖥️ Metasploitable 2 Enumeration

Performed full attack surface analysis:

- Identified open services (FTP, SMB, HTTP, SSH)
- Discovered **anonymous SMB shares with read/write access**
- Enumerated web directories including:
  - `/phpMyAdmin`
  - `/dav`
  - `/test`
- Detected outdated services:
  - Apache 2.2.8
  - PHP 5.2.4
  - vsFTPd 2.3.4
- Confirmed vulnerabilities using:
  - Nikto
  - Manual banner grabbing (Netcat)

---

# 🔍 What I've Covered

## Reconnaissance & Enumeration

- Network discovery using Nmap  
- Full port scanning  
- Service/version detection  
- SMB share enumeration  
- HTTP directory brute forcing (dirb)  
- Vulnerability scanning (Nikto)  
- Manual enumeration (Netcat)  

---

## ⚙️ Attacker Infrastructure Setup

- Python HTTP server for payload delivery  
- Reverse shell preparation  
- Basic service hosting  

---

# 🧰 Tools Used

- Nmap  
- Dirb  
- Nikto  
- Netcat  
- SMBClient  
- FTP  
- Python HTTP Server  
- Linux CLI tools  

---

# 📂 Repository Structure

```bash
.
├── 02_Enumeration/     # Service enumeration notes
├── 05_Labs/            # Completed lab walkthroughs
├── 06_Cheat_Sheets/    # Quick command references
├── screenshots/        # Evidence from labs
└── README.md

🧠 Methodology

My workflow follows a structured penetration testing process:

Reconnaissance
Service Enumeration
Attack Surface Analysis
Vulnerability Identification
Exploitation
Post-Exploitation
Documentation

## 🧩 Skills Demonstrated (With Evidence)

| Skill | Evidence |
|------|--------|
| SMB Enumeration | Anonymous share access discovered |
| Web Enumeration | Hidden directories found using dirb |
| Vulnerability Detection | Outdated Apache & PHP identified |
| Manual Enumeration | Banner grabbing using netcat |
| Linux Navigation | Retrieved files via restricted shell |

📈 Progress Status

Current Phase: Enumeration & Attack Surface Analysis

Next Focus:

Service exploitation
Reverse shells
Privilege escalation

📸 Documentation Approach

Each lab includes:

Commands used
Output analysis
Screenshots
Key findings
Lessons learned

🧠 Learning Philosophy
Understand tools deeply, not just use them
Focus on manual techniques
Document everything professionally
Build real-world thinking

🔗 Follow My Journey
Medium: https://medium.com/@akintayoolamide6/
LinkedIn: www.linkedin.com/in/olamide-akintayo-270290124

⚠️ Disclaimer

This repository is for educational purposes only.
All activities are conducted in a controlled lab environment.

🏁 Goal

Earn the eJPT certification and build a strong foundation for a career in penetration testing.
