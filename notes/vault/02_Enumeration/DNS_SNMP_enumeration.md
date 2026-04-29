# DNS & SNMP Enumeration

## 1. DNS Enumeration

DNS enumeration was attempted using `dnsrecon` against the target IP.

### Command Used:

```bash
dnsrecon -d 192.168.213.129
```

### Result:

- Error: Could not resolve domain
    

### Reason:

`dnsrecon` requires a **valid domain name**, not an IP address.

### Correct Usage Example:

```bash
dnsrecon -d example.com
```

---

### Key Takeaway:

- DNS enumeration is **domain-based**, not IP-based.
    
- On internal lab machines (e.g., Metasploitable2), DNS is usually not the primary focus.
    

---

## 2. SNMP Enumeration

SNMP was tested to check for exposed network management services.

---

### Step 1: Check SNMP Port

```bash
nmap -sU -p 161 192.168.213.129
```

### Result:

- Port 161/udp → **closed**
    

### Interpretation:

- SNMP service is not running or is blocked.
    

---

### Step 2: SNMP Walk Attempt

```bash
snmpwalk -v 1 -c public 192.168.213.129
```

### Result:

- Timeout: No response from target
    

---

## 3. Final Findings

- DNS enumeration: Not applicable (IP used instead of domain)
    
- SNMP port (161): Closed
    
- SNMP service: Not available
    

---

## 4. Security Implications

- No SNMP exposure → no system information leakage via SNMP
    
- No DNS misconfiguration observed on this host
    
- These services do not represent attack vectors on this target
    

---

## 5. Key Takeaways

- Always ensure correct tool usage (DNS tools require domains, not IPs)
    
- SNMP must be confirmed open before enumeration attempts
    
- Not all services will be available on every target — documenting absence is still valid enumeration
    

---

## Personal Note

Even though no data was retrieved, confirming the absence of services is still part of professional enumeration. Knowing what is NOT available helps narrow down attack paths.