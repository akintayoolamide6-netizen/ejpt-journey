# SMB Commands Cheat Sheet

Quick reference for SMB enumeration using smbclient.

---

## 🔍 Scan for Shares (Nmap)

```bash
nmap -p 139,445 --script=smb-enum-shares <target_IP>
```

---

## 📋 List Shares

```bash
smbclient -L //<target_IP> -N
```

Lists all available shares using anonymous login.

---

## 🔗 Connect to Share

```bash
smbclient //<target_IP>/<sharename> -N
```

Example:

```bash
smbclient //<target_IP>/public -N
```

---

## 📂 List Files

```bash
ls
```

---

## 📁 Navigate

```bash
cd <directory>
```

---

## 📥 Download Files

```bash
get <filename>
```

Download all:

```bash
mget *
```

---

## ❌ Exit

```bash
exit
```

---

## ⚠️ Notes

- `-N` = no password (anonymous login)
    
- Not all shares are accessible
    
- Always test:
    
    - Listing shares
        
    - Accessing shares
        
    - Downloading files
        

---

## 🧠 Exam Tip (eJPT)

Always check:

- Can I list shares?
    
- Can I access any share?
    
- Can I download files?
    

If yes → high chance of finding credentials or sensitive data.