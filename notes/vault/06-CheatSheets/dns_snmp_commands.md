# DNS & SNMP Cheat Sheet

## 🌐 DNS Enumeration

### Correct Usage

```bash
dnsrecon -d example.com
```

### Zone Transfer Attempt

```bash
dnsrecon -d example.com -t axfr
```

### Subdomain Brute Force

```bash
dnsrecon -d example.com -t brt -D /usr/share/wordlists/dnsmap.txt
```

---

### ⚠️ Important Notes

- DNS tools require **domain names, not IP addresses**
    
- Common mistake: running dnsrecon on internal IPs
    
- Best used during external reconnaissance
    

---

## 📡 SNMP Enumeration

### Check SNMP Availability

```bash
nmap -sU -p 161 <target_IP>
```

### SNMP Walk (Basic)

```bash
snmpwalk -v 1 -c public <target_IP>
```

### SNMP Walk (More Stable Version)

```bash
snmpwalk -v 2c -c public <target_IP>
```

---

## ⚠️ SNMP Notes

- SNMP uses UDP port 161
    
- Default community string = `public`
    
- If closed → SNMP enumeration is not possible
    
- If open → can leak system information (users, processes, configs)
    

---

## 🧠 Exam Tip (eJPT)

Always confirm:

- Is port open? (nmap first)
    
- Is service responding? (snmpwalk test)
    
- If not available → document and move on
    

Absence of service is still valid enumeration.