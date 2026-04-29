# Web Enumeration Cheat Sheet

## 🔍 dirb (Directory Brute Force)

### Basic Scan

```bash
dirb http://<target_IP>
```

### Use Custom Wordlist

```bash
dirb http://<target_IP> /usr/share/wordlists/dirb/common.txt
```

### Ignore Specific Status Codes

```bash
dirb http://<target_IP> -N 403
```

### Output to File

```bash
dirb http://<target_IP> -o output.txt
```

---

## 🛠️ nikto (Web Vulnerability Scanner)

### Basic Scan

```bash
nikto -h http://<target_IP>
```

### Scan Specific Port

```bash
nikto -h http://<target_IP>:8080
```

### Force SSL

```bash
nikto -h https://<target_IP>
```

### Output to File

```bash
nikto -h http://<target_IP> -o report.txt
```

---

## ⚠️ Notes

- dirb = finds hidden directories/files
    
- nikto = finds known vulnerabilities
    
- Always manually verify findings in a browser
    
- Look for:
    
    - Login pages
        
    - Admin panels
        
    - Config files
        
    - Upload functionality
        

---

## 🧠 Exam Tip (eJPT)

Always run:

- dirb → for hidden paths
    
- nikto → for quick vulnerability overview
    

Then manually explore everything you find.
# Web Enumeration Additions

## 🔍 Manual Discovery

### View Page Source

- CTRL + U
    
- Look for:
    
    - Comments
        
    - Hidden credentials
        

---

## 📁 Common Hidden Paths

```bash
/login.php
/admin
/robots.txt
/assets/
```

---

## 🧪 Command Execution (Web Shell)

### Basic Commands

```bash
ls
pwd
cd
```

---

### File Reading (if cat is blocked)

```bash
less file.txt
more file.txt
head file.txt
tail file.txt
```

---

## 🧠 Notes

- Always test common login paths manually
    
- Directory listing = sensitive exposure
    
- robots.txt often contains clues in CTFs