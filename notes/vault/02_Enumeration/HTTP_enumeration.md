# HTTP Enumeration

## 1. Initial Web Recon

The target web application was accessed via:

```bash
http://<target_IP>
```

### Observations:

- Apache web server running
    
- Default web application content visible
    
- Multiple web applications discovered through enumeration
    

---

## 2. Directory Enumeration (dirb)

Command used:

```bash
dirb http://<target_IP>
```

### Key Findings:

- `/cgi-bin/` → 403 Forbidden
    
- `/dav/` → WebDAV directory (important attack surface)
    
- `/phpMyAdmin/` → Database management interface exposed
    
- `/test/` → Directory listing enabled
    
- `/twiki/` → Web-based collaboration platform
    
- `/phpinfo.php` → PHP configuration disclosure page
    
- `/server-status` → Restricted Apache status page
    

---

### Interpretation:

- Multiple administrative and sensitive interfaces are exposed.
    
- `/phpMyAdmin/` is a high-value target for database access.
    
- `/phpinfo.php` leaks system configuration details.
    
- `/test/` directory is listable, which may expose files.
    

---

## 3. Vulnerability Scanning (nikto)

Command used:

```bash
nikto -h http://<target_IP>
```

### Key Findings:

- Server: Apache/2.2.8 (Ubuntu)
    
- PHP Version: 5.2.4 (outdated)
    
- Directory indexing enabled (`/icons/`, `/doc/`, `/test/`)
    
- HTTP TRACE method enabled (potential XST vulnerability)
    
- phpMyAdmin publicly accessible
    
- Missing security headers:
    
    - Content-Security-Policy
        
    - X-Content-Type-Options
        
    - Strict-Transport-Security
        
    - Referrer-Policy
        

---

### Security Implications:

- Outdated Apache and PHP versions may contain known exploits.
    
- Directory listing exposes internal structure.
    
- TRACE method can be abused for Cross-Site Tracing (XST).
    
- Missing headers indicate weak security hardening.
    

---

## 4. Key Attack Surfaces Identified

- `/phpMyAdmin/` → Database access interface
    
- `/dav/` → WebDAV upload capability (potential file upload attack)
    
- `/twiki/` → Web application (possible auth bypass or RCE paths)
    
- `/test/` → Directory listing enabled
    
- `/phpinfo.php` → Sensitive system information disclosure
    

---

## 5. Key Takeaways

- HTTP enumeration revealed multiple exploitable web services.
    
- The presence of phpMyAdmin is a critical pivot point.
    
- Directory listing significantly increases attack surface visibility.
    
- Outdated software versions increase exploitability.
    
- Web enumeration is one of the most important phases in penetration testing.
    

---

## Personal Note

This phase demonstrates how a single web server can expose multiple attack vectors. Proper enumeration reveals not just one vulnerability, but an entire ecosystem of misconfigurations and outdated services that can be chained for exploitation.