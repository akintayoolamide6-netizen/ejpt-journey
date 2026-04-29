# FTP Commands Cheat Sheet

A quick reference of essential FTP commands used during enumeration and basic interaction.

---

## 🔑 Connection

```bash
ftp <target_IP>
```

Connects to the FTP server.

---

## 📂 Listing Files

```bash
ls
```

Lists files in the current directory.

```bash
ls -la
```

Lists all files (including hidden ones) with detailed information.

---

## 📥 Downloading Files

```bash
get <filename>
```

Downloads a single file from the FTP server to the local machine.

```bash
mget *
```

Downloads multiple files at once.

---

## 📤 Uploading Files

```bash
put <filename>
```

Uploads a file from the local machine to the FTP server.

> ⚠️ Note: Upload may fail if the server is read-only (e.g., `553 Could not create file`).

---

## 📁 Navigation

```bash
cd <directory>
```

Moves into a directory on the FTP server.

```bash
pwd
```

Displays the current directory on the server.

---

## ❌ Exit Connection

```bash
bye
```

Closes the FTP session.

---

## ⚠️ Important Notes

- FTP is **not a full shell** — Linux commands like `echo`, `cat`, etc., will NOT work inside FTP.
    
- Always create/edit files **locally on Kali**, then upload using `put`.
    
- If `ls` shows nothing, the directory may still be valid but empty.
    
- Always test:
    
    - Anonymous login
        
    - File access
        
    - Write permissions
        

---

## 🧠 Exam Tip (eJPT)

Focus on these actions:

- Can I log in anonymously?
    
- Can I read files?
    
- Can I upload files?
    

These three checks determine your next move.