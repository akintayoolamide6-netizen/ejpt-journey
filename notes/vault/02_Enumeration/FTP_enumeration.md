# FTP Enumeration

## 1. Detecting FTP Version

To identify the FTP service and its version, I used Nmap service detection:

```bash
nmap -p 21 -sV <target_IP>
```

### Example Output:

```
21/tcp open  ftp  vsftpd 2.3.4
```

### Interpretation:

- Port 21 is open, confirming FTP is running.
    
- The service version is **vsftpd 2.3.4**.
    

### Why This Matters:

Identifying the version is critical because:

- It allows mapping to known vulnerabilities.
    
- It guides the next step (e.g., searching for exploits using `searchsploit`).
    
- Some versions (like vsftpd 2.3.4) are known to be vulnerable and exploitable.
    

---

## 2. Testing Anonymous Login

To check if anonymous access is enabled, I used both automated and manual methods.

### Nmap Script:

```bash
nmap --script=ftp-anon -p 21 <target_IP>
```

### Manual Login:

```bash
ftp <target_IP>
```

Login credentials used:

```
Username: anonymous
Password: anonymous
```

### Expected Output (Successful Login):

```
230 Login successful
```

### Result:

- Anonymous login was **successfully allowed**.
    

### Why This Matters:

Anonymous login can expose sensitive files or allow unauthorized access. It is often a misconfiguration and a potential entry point for attackers.

---

## 3. File Enumeration

After gaining access, I attempted to list and explore available files.

### Commands Used:

```bash
ls
ls -la
cd <directory>
```

### Result:

- No files were found in the directory.
    
- The directory appeared empty except for `.` and `..`.
    

### Interpretation:

- There are **no publicly accessible files** available via anonymous FTP.
    
- This reduces the likelihood of finding credentials or sensitive data at this stage.
    

---

## 4. Write Access Test

To check if the FTP server allows file uploads, I tested write permissions.

### Step 1: Create a test file locally

```bash
echo "test" > test.txt
```

### Step 2: Attempt upload in FTP

```bash
put test.txt
```

### Output:

```
553 Could not create file.
```

### Result:

- File upload was **denied**.
    

### Interpretation:

- The FTP server is **read-only**.
    
- No ability to upload files means:
    
    - No web shell upload
        
    - No direct file-based exploitation via FTP
        

---

## 5. Findings Summary

- FTP Service: Running (vsftpd 2.3.4)
    
- Anonymous Login: Allowed
    
- Files Found: None
    
- Write Access: Denied
    

---

## 6. Key Takeaways

Even though no files were found, this enumeration phase is still valuable:

- Anonymous access confirms a misconfiguration, even if limited.
    
- Lack of files indicates no immediate data exposure.
    
- No write access prevents direct FTP-based exploitation.
    
- The service version (vsftpd 2.3.4) becomes the **primary attack vector moving forward**.
    

---

## 7. Next Steps

Since FTP enumeration did not yield files or write access, the next logical steps are:

- Search for known exploits related to the FTP version:
    
    ```bash
    searchsploit vsftpd 2.3.4
    ```
    
- Continue enumeration on other open ports and services.
    

---

## Personal Note

This step reinforced an important lesson:  
**Enumeration is not about always finding something — it is about understanding what is available and what is not.**