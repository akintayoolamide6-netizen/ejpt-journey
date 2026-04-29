# TryHackMe – Pickle Rick (Enumeration-Focused Lab)

## 🎯 Objective

Perform full enumeration on the target system and retrieve the three hidden ingredients by analyzing the web application and interacting with a command execution interface.

---

## 🔍 1. Initial Recon

### Action:

Visited target IP in browser.

### Observation:

- Web page loaded with Rick and Morty theme
    
- No obvious login form
    
- Page hinted at a story-based challenge
    

---

## 🔍 2. Source Code Inspection

### Action:

Viewed page source (CTRL + U)

### Findings:

- Hidden comment revealed a username:
    

```html
Username: R1ckRul3s
```

### Importance:

- This provided a valid credential component (username)
    

---

## 🔍 3. robots.txt Enumeration

### Action:

Visited:

```bash
/robots.txt
```

### Result:

```
Wubbalubbadubdub
```

### Interpretation:

- Likely a password or key phrase
    

---

## 🔍 4. Directory Enumeration

### Command:

```bash
dirb http://<target_IP>
```

### Findings:

- /assets/ (directory listing enabled)
    
- /robots.txt
    
- /index.html
    

### Action:

Visited `/assets/` and inspected files (images, scripts)

### Importance:

- Confirmed misconfiguration (directory listing enabled)
    

---

## 🔍 5. Login Panel Discovery

### Action:

Manually tested common paths

```bash
/login.php
```

### Result:

- Login portal discovered
    

---

## 🔐 6. Authentication

### Credentials Used:

- Username: R1ckRul3s
    
- Password: Wubbalubbadubdub
    

### Result:

- Access granted to command execution panel
    

---

## 🖥️ 7. Command Execution (Web Shell)

### Observation:

- Terminal-like interface
    
- Some commands restricted (e.g., `cat`)
    

---

## 🧪 8. Enumeration via Commands

### Commands Used:

```bash
ls
pwd
ls /home
ls /var/www/html
```

### Key Learning:

- Enumeration is required even after access
    
- Need to explore file system manually
    

---

## 🧠 9. Reading Files (Bypassing Restrictions)

### Problem:

`cat` command restricted

### Solution:

Used alternative commands:

```bash
less <filename>
more <filename>
```

### Importance:

- Demonstrates adaptability in restricted environments
    

---

## 🏁 10. Ingredient Discovery

### Method:

- Navigated directories
    
- Located `.txt` files
    
- Read contents using `less`
    

### Final Result:

- Successfully retrieved ingredient(s)
    
- Example answer:
    

```
mr. meeseek hair
```

---

## 🧠 Lessons Learned

- Always inspect page source for hidden data
    
- robots.txt can expose sensitive information
    
- Directory enumeration reveals hidden attack surface
    
- Manual path guessing is critical (/login.php)
    
- Restricted shells require alternative command usage
    
- Enumeration does not stop after gaining access
    

---

## 🚀 Key Takeaways

- Enumeration is the most important phase in pentesting
    
- Small clues (comments, robots.txt) can lead to full compromise
    
- Understanding systems > running tools blindly
    
- Web-based shells still require Linux knowledge
    

---

## 🧾 Commands Summary

```bash
nmap -sC -sV <IP>
nmap -p- <IP>
dirb http://<IP>
ls
pwd
ls /home
ls /var/www/html
less <file>
```

---

## 📸 Screenshots to Include

- nmap scan results
    
- dirb output
    
- page source (username found)
    
- robots.txt output
    
- /assets/ directory listing
    
- login page
    
- command panel
    
- ingredient file output
    

---

## 💡 Personal Reflection

This lab emphasized the importance of manual enumeration and thinking critically about discovered information. Instead of relying solely on tools, understanding how to interpret clues led to successful completion.

This approach directly applies to real-world penetration testing and eJPT exam scenarios.