# Manual Enumeration (Netcat)

## 1. Overview

Manual enumeration involves directly connecting to open ports using Netcat (`nc`) to retrieve service banners and validate automated scan results.

This helps confirm:

- Service presence
    
- Version information
    
- Server behavior
    

---

## 2. HTTP Enumeration (Port 80)

### Command:

```bash
nc 192.168.213.129 80
```

### Request sent:

```http
HEAD / HTTP/1.0
```

### Result:

```http
HTTP/1.1 200 OK
Server: Apache/2.2.8 (Ubuntu) DAV/2
X-Powered-By: PHP/5.2.4-2ubuntu5.10
Content-Type: text/html
```

### Interpretation:

- Apache web server is running
    
- Version: 2.2.8 (outdated)
    
- PHP version exposed: 5.2.4 (outdated)
    
- WebDAV module enabled (DAV/2)
    

---

## 3. FTP Enumeration (Port 21)

### Command:

```bash
nc 192.168.213.129 21
```

### Result:

```text
220 (vsFTPd 2.3.4)
```

### Interpretation:

- FTP service is active
    
- Version: vsFTPd 2.3.4
    
- Version exposure is useful for vulnerability research
    

---

## 4. SSH Enumeration (Port 22)

### Command:

```bash
nc 192.168.213.129 22
```

### Result:

```text
SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1
```

### Interpretation:

- SSH service is running
    
- Version is outdated
    
- OS hint: Debian-based system
    

---

## 5. SMB Check (Port 445)

### Command:

```bash
nc 192.168.213.129 445
```

### Result:

- No readable banner returned
    
- Connection attempt confirms service is reachable but does not expose banner via netcat
    

---

## 6. Key Findings Summary

|Service|Version|Status|
|---|---|---|
|HTTP|Apache 2.2.8 / PHP 5.2.4|Exposed|
|FTP|vsftpd 2.3.4|Exposed|
|SSH|OpenSSH 4.7|Exposed|
|SMB|Samba present|No banner|

---

## 7. Key Takeaways

- Manual enumeration confirms automated scan results
    
- Service banners reveal outdated software versions
    
- Web server exposes additional modules (WebDAV)
    
- Not all services return readable banners via Netcat
    
- Manual interaction helps validate real attack surface
    

---

## Personal Insight

Manual enumeration provides a deeper understanding of how services respond at the network level. Unlike automated tools, it shows raw service behavior and helps confirm real attack vectors before exploitation.