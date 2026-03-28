# Nmap Scan Types — My Practical Notes (Metasploitable Lab)

## Lab Setup

**Attacker:** Kali Linux  
**Target:** Metasploitable 2  
**Target IP:** `192.168.246.131`

---

# What Happened During My Scan

While running my scans, I noticed:

- At some point, **Host seems down / 0 hosts up**
    
- This happened because **Metasploitable 2 was powered off**
    
- After turning it back on, my scans worked again
    

Example I saw:

```
Host seems down. If it is really up, try -Pn
```

After restarting Metasploitable 2, I ran the scan again and it worked.

This helped me understand:

- If host is down → Check VM first
    
- If host is up but blocked → Use `-Pn`
    

---

# My Scan Commands (What I Practiced)

I ran:

```bash
nmap -sV -O -sSU 192.168.246.131
```

Then:

```bash
nmap -sV -O -Pn 192.168.246.131
```

Then:

```bash
nmap -sV -O -sS -sU 192.168.246.131
```

Then:

```bash
nmap -sV -O -sT 192.168.246.131
```

Finally:

```bash
nmap -sV -O -sT 192.168.246.131
```

Final scan worked after target came back online.

---

# Scan Types — My Refresher Table

| Scan Type        | Command Example             | When I Use It               | What It Does          |
| ---------------- | --------------------------- | --------------------------- | --------------------- |
| TCP SYN Scan     | `nmap -sS 192.168.246.131`  | Default scan / stealth scan | Fast and less noisy   |
| TCP Connect Scan | `nmap -sT 192.168.246.131`  | When SYN scan fails         | Full TCP connection   |
| UDP Scan         | `nmap -sU 192.168.246.131`  | Check UDP ports             | Slower but useful     |
| Service Version  | `nmap -sV 192.168.246.131`  | Identify services           | Shows version numbers |
| OS Detection     | `nmap -O 192.168.246.131`   | Identify OS                 | Shows Linux / Windows |
| Ping Scan        | `nmap -sP 192.168.246.0/24` | Find live hosts             | Host discovery        |
| No Ping Scan     | `nmap -Pn 192.168.246.131`  | Host appears down           | Skip host discovery   |

---

# Differences (Simple)

| Option | Difference                |
| ------ | ------------------------- |
| -sS    | Half-open stealth scan    |
| -sT    | Full TCP connection       |
| -sU    | UDP scan                  |
| -sV    | Service version detection |
| -O     | OS detection              |
| -sP    | Find live hosts           |
| -Pn    | Skip host discovery       |

---

# My Final Working Command

This worked best for me:

```bash
nmap -sV -O -sT 192.168.246.131
```

This gave me:

- Open ports
    
- Service versions
    
- OS detection
    

---

# What I Discovered on Metasploitable 2

Open Ports I Found:

- 21 → FTP
    
- 22 → SSH
    
- 23 → Telnet
    
- 25 → SMTP
    
- 80 → HTTP
    
- 139 → NetBIOS
    
- 445 → SMB
    
- 3306 → MySQL
    
- 5432 → PostgreSQL
    
- 5900 → VNC
    
- 6667 → IRC
    
- 8180 → Tomcat
    

This tells me:

- Many services running
    
- Large attack surface
    
- Good practice machine
    

---

# My Learning Takeaways

- If host is down → Check VM first
    
- Use `-Pn` if ping blocked
    
- `-sV` gives more details
    
- `-O` helps identify OS
    
- Combine scans for better results
    

---

# My Go-To Commands

Find host:

```bash
nmap -sP 192.168.246.0/24
```

Quick scan:

```bash
nmap 192.168.246.131
```

Detailed scan:

```bash
nmap -sV -O 192.168.246.131
```

Full scan:

```bash
nmap -sS -sU -sV -O 192.168.246.131
```

---

# Personal Reminder

Always check:

- Target VM running
    
- Same network
    
- Correct IP
    

Before scanning.