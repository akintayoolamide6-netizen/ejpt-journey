# Port Scanning — My Personal Refresher Notes

## What is a Port Scan?

A **port scan** is when I check a target machine to see which **ports (doors)** are open.

This helps me:

- Know what services are running
    
- Understand the target better
    
- Decide my next step
    

For example, from my scan:

- Port 22 → SSH
    
- Port 80 → HTTP
    
- Port 445 → SMB
    

This tells me **what I can try next**.

I usually start with a port scan before doing anything else.

---

## What `-sV` Does

`-sV` helps me **see the version of services running** on open ports.

Example I ran:

```bash
nmap -sV 192.168.246.131
```

This showed things like:

- vsftpd 2.3.4
    
- OpenSSH 4.7
    
- Apache 2.2.8
    

This is very useful because **older versions may have vulnerabilities**.

So whenever I want more information about services, I use `-sV`.

---

## What `-O` (Capital O) Does

`-O` helps me **detect the operating system** of the target.

Example I ran:

```bash
nmap -sV -O 192.168.246.131
```

From my scan, I saw:

- Linux 2.6.X
    
- Ubuntu
    

This tells me:

- What OS I'm attacking
    
- What exploits might work
    

I use `-O` when I want **more information about the target system**.

---

## What `-o` (Small o) Does

`-o` helps me **save my scan results**.

Example:

```bash
nmap -sV -o scan.txt 192.168.246.131
```

I use this when:

- I want to keep notes
    
- I want to review later
    
- I'm doing lab practice
    

This helps me **stay organized**.

---

## What `-sP` Does

`-sP` helps me **find live machines on the network**.

Example I ran:

```bash
nmap -sP 192.168.246.132/24
```

From my scan, I found:

- 192.168.246.131
    
- 192.168.246.132
    
- 192.168.246.254
    

This helps me know:

- Which machines are alive
    
- Which one to scan next
    

I usually run this **before port scanning**.

---

## My Typical Workflow

1. Find live hosts
    

```bash
nmap -sP 192.168.246.132/24
```

2. Scan ports
    

```bash
nmap 192.168.246.131
```

3. Get service versions
    

```bash
nmap -sV 192.168.246.131
```

4. Detect OS
    

```bash
nmap -sV -O 192.168.246.131
```

---

## My Quick Summary

- Port scan → Find open ports
    
- `-sV` → Show service version
    
- `-O` → Detect operating system
    
- `-o` → Save scan results
    
- `-sP` → Find live hosts
    

---

## My Real Example (Metasploitable Lab)

Target:

```
192.168.246.131
```

I discovered:

- FTP
    
- SSH
    
- Telnet
    
- HTTP
    
- SMB
    
- MySQL
    

This tells me:

- This machine has many services
    
- More attack surface
    
- More learning opportunities