# SMB Enumeration

## 1. Scanning SMB Ports

To identify SMB services and enumerate shares:

```bash
nmap -p 139,445 --script=smb-enum-shares <target_IP>
```

### Result:

- Ports 139 and 445 are open.
    
- SMB service is running (Samba 3.0.20 on Metasploitable2).
    

---

## 2. Enumerating Shares

Command used:

```bash
smbclient -L //<target_IP> -N
```

### Output:

```bash
Sharename       Type      Comment
---------       ----      -------
print$          Disk      Printer Drivers
tmp             Disk      oh noes!
opt             Disk      
IPC$            IPC       IPC Service
ADMIN$          IPC       IPC Service
```

### Key Observation:

- Anonymous login was **successful**.
    
- Multiple shares are available.
    

---

## 3. Access Control Analysis

From Nmap results:

- `tmp` → **READ/WRITE access (anonymous)**
    
- `IPC$` → READ/WRITE (but not useful for file access)
    
- `opt`, `print$`, `ADMIN$` → No anonymous access
    

### Important Finding:

The `tmp` share is **world-accessible and writable**, which is a serious misconfiguration.

---

## 4. Connecting to the Share

Command used:

```bash
smbclient //<target_IP>/tmp -N
```

Access was successful.

---

## 5. File Enumeration

Commands used inside smbclient:

```bash
ls
cd <directory>
```

### Files Found:

```bash
.ICE-unix/
.X11-unix/
.X0-lock
5186.jsvc_up
```

---

## 6. File Analysis & Interpretation

### Observations:

- `.ICE-unix` and `.X11-unix`  
    → System-related directories (X server communication sockets)  
    → Not useful for direct exploitation
    
- `.X0-lock`  
    → Indicates an active X session  
    → Suggests GUI processes are running
    
- `5186.jsvc_up`  
    → Likely related to a running service (possibly Apache Tomcat or similar)  
    → Could indicate a backend service worth investigating
    

---

## 7. Key Security Finding

The `tmp` share allows:

- Anonymous access ✅
    
- Read access ✅
    
- Write access ✅
    

### Why This is Critical:

This means:

- Anyone can upload files
    
- Possible to upload:
    
    - Reverse shells
        
    - Malicious scripts
        
- Potential path to remote code execution (RCE)
    

---

## 8. Next Steps (Exploitation Path)

Based on findings, next logical actions:

- Attempt file upload:
    
    ```bash
    put test.txt
    ```
    
- Check if uploaded files are accessible via:
    
    - Web server (if `/tmp` is mapped)
        
    - Other services
        
- Investigate running services related to discovered files (e.g., `5186.jsvc_up`)
    

---

## 9. Key Takeaways

- SMB enumeration revealed a **high-risk misconfiguration**
    
- Writable shares are a major attack vector
    
- Even system-looking files can give clues about running services
    
- This is a strong pivot point for exploitation
    

---

## Personal Note

Unlike FTP, SMB provided meaningful access and a writable location.  
This highlights the importance of enumerating multiple services — if one fails, another may expose a critical weakness.