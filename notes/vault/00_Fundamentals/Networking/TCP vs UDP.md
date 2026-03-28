# TCP vs UDP — Quick Refresher (Pentesting Notes)

## What is a Port?

A **Port** is a communication endpoint on a computer.

- **IP Address** = House Address
    
- **Port** = Room number in the house
    

Example:  
`192.168.1.1:80`

- `192.168.1.1` → IP Address
    
- `80` → Port (Web traffic)
    

Ports allow multiple services to run on one system at the same time.

---

# TCP vs UDP (Simple Definition)

## TCP (Transmission Control Protocol)

TCP is **Reliable but Slower**

- Connection-oriented (3-way handshake)
    
- Reliable delivery
    
- Packets arrive in order
    
- Retransmits lost packets
    

### TCP = Accuracy > Speed

### Real-Life Examples

- Website browsing
    
- File downloads
    
- Emails
    
- SSH login
    

---

## UDP (User Datagram Protocol)

UDP is **Fast but Unreliable**

- Connectionless
    
- No acknowledgement
    
- No retransmission
    
- Faster than TCP
    

### UDP = Speed > Accuracy

### Real-Life Examples

- Live streaming
    
- Video calls
    
- Online gaming
    
- DNS queries
    

---

# TCP vs UDP Quick Table

|Feature|TCP|UDP|
|---|---|---|
|Speed|Slower|Faster|
|Reliability|High|Low|
|Connection|Yes|No|
|Retransmission|Yes|No|
|Use Case|Downloads, Websites|Streaming, Gaming|

---

# Common Ports for Pentesting

## Most Important Ports to Memorize

### TCP Ports

|Port|Service|What it Does|
|---|---|---|
|21|FTP|File Transfer|
|22|SSH|Secure Remote Login|
|23|Telnet|Remote Login (Unsecured)|
|25|SMTP|Send Email|
|53|DNS|Domain Name Resolution|
|80|HTTP|Website Traffic|
|110|POP3|Receive Email|
|139|NetBIOS|Windows File Sharing|
|143|IMAP|Receive Email|
|443|HTTPS|Secure Website|
|445|SMB|Windows File Sharing|
|3389|RDP|Remote Desktop|

---

### UDP Ports

|Port|Service|What it Does|
|---|---|---|
|53|DNS|Domain Name Resolution|
|67|DHCP|Assign IP Address|
|68|DHCP|Receive IP Address|
|69|TFTP|Simple File Transfer|
|123|NTP|Time Sync|
|161|SNMP|Network Monitoring|
|137|NetBIOS|Windows Networking|

---

# Easy Memory Trick

- **HTTP → 80** → Websites
    
- **HTTPS → 443** → Secure Websites
    
- **SSH → 22** → Remote login
    
- **FTP → 21** → File transfer
    
- **DNS → 53** → Domain names
    
- **RDP → 3389** → Remote desktop
    

---

# TCP 3-Way Handshake (Quick Note)

1. SYN → Client sends request
    
2. SYN-ACK → Server responds
    
3. ACK → Connection established
    

Connection Established ✅

---

# When to Use TCP vs UDP

### Use TCP When:

- Accuracy is important
    
- File transfer
    
- Web browsing
    
- Email
    

### Use UDP When:

- Speed is important
    
- Streaming
    
- Gaming
    
- DNS
    

---

# Pentesting Tip

When scanning ports:

- Open **22** → Try SSH access
    
- Open **80/443** → Web vulnerabilities
    
- Open **445** → SMB vulnerabilities
    
- Open **3389** → RDP attack surface
    

---

# Quick Summary

- TCP = Reliable but slower
    
- UDP = Fast but unreliable
    
- Port = Service door
    
- Memorize common ports for pentesting
    

---

# Must-Memorize (Top 10)

```
21  - FTP
22  - SSH
23  - Telnet
25  - SMTP
53  - DNS
80  - HTTP
110 - POP3
139 - NetBIOS
443 - HTTPS
3389 - RDP
```