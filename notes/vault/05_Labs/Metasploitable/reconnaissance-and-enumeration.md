# Reconnaissance and Enumeration

## Lab Setup

### Environment

Attacker Machine: Kali Linux  
Target Machine: Metasploitable 2  
Virtualization Platform: VMware Workstation

### Purpose

Create a controlled penetration testing environment for vulnerability assessment and exploitation practice.

---

# Network Discovery

## Command Used

nmap -sn 192.168.246.132/24

## Purpose

Identify active hosts on the network before beginning enumeration.

## Result

Multiple hosts were discovered within the subnet.

## Lesson Learned

Always perform network discovery before targeting a specific machine. This helps identify valid targets and reduces unnecessary scanning.

---

# Nmap Troubleshooting

## Issue

During initial scanning, the target appeared offline.

## Error

Host seems down. If it is really up, try -Pn

## Solution

Used the -Pn flag to skip host discovery.

## Lesson Learned

Some systems block ICMP ping requests, requiring the use of the -Pn flag to force scanning.

---

# Service Discovery Scan

## Command Used

nmap -sV -sC 192.168.246.131

## Purpose

Perform service version detection and run default enumeration scripts.

## Findings

- Multiple open ports detected
    
- Samba service identified
    
- Host operating system detected as Unix/Linux
    
- Hostname identified as metasploitable
    

## Security Observation

The system exposes multiple services which increases the attack surface.

---

# Full Enumeration

## Command Used

nmap -sV -O 192.168.246.131

## Description

Performed service version detection and operating system identification.

## Result

Multiple vulnerable services identified including:

- FTP
    
- SSH
    
- Telnet
    
- SMTP
    
- HTTP
    
- SMB
    
- MySQL
    
- PostgreSQL
    
- VNC
    
- Tomcat
    

## Security Observation

Large attack surface due to multiple exposed services.

---

# Full Nmap Enumeration

## Command Used

nmap -sS -sV -O 192.168.246.131

## Flag Explanation

-sS : SYN stealth scan  
-sV : Service version detection  
-O : Operating system detection

## Purpose

Perform comprehensive enumeration to identify services and operating system.

## Result

Extensive service exposure confirmed, increasing potential exploitation paths.

---

# SMB Enumeration — Metasploitable 2

## Command Used

nmap --script smb-enum-users -p445 192.168.246.131

## Purpose

Enumerate users via SMB service.

## Users Discovered

- backup
    
- bin
    
- bind
    
- daemon
    
- dhcp
    
- distccd
    
- ftp
    
- games
    
- gnats
    
- irc
    
- klog
    
- libuuid
    
- list
    

## Analysis

Multiple system accounts were discovered through SMB enumeration.

This indicates:

- Weak SMB configuration
    
- Information disclosure vulnerability
    
- Potential credential attack targets
    

---

# Key Findings

- Multiple open ports discovered
    
- Numerous outdated services running
    
- SMB information disclosure vulnerability
    
- Large attack surface identified
    

---

# Next Steps

- SMB share enumeration
    
- Password brute force attempts
    
- SMB login attempts
    
- Service-specific vulnerability analysis
    

---

# Summary

The reconnaissance and enumeration phase revealed a highly vulnerable target with multiple exposed services. This significantly increases the likelihood of successful exploitation in subsequent phases.