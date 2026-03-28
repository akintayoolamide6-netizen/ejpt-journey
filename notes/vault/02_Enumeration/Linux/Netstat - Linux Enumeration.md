# Netstat — Quick Refresher (Pentesting Notes)

# What is Netstat?

`**netstat` is a command-line tool used to:**

- **View open ports**
    
- **Check listening services**
    
- **View active connections**
    
- **Analyze network activity**
    

Pentesters use `netstat` for **local enumeration**.

---

# Basic Command

```bash
netstat
```

This shows:

- TCP connections
    
- UDP connections
    
- Active connections
    
- Listening services
    

---

# Most Important Netstat Commands

## 1. Show Open Ports (Most Common)

```bash
netstat -tuln
```

### Meaning

|Option|Meaning|
|---|---|
|-t|TCP ports|
|-u|UDP ports|
|-l|Listening ports|
|-n|Numeric format|

This command shows **open ports only**.

---

## 2. Show Program Using Port (Pentester Favorite)

```bash
sudo netstat -tulnp
```

This shows:

- Port number
    
- Protocol
    
- Process name
    
- PID
    

Example:

```
tcp   0   0   0.0.0.0:22   0.0.0.0:*   LISTEN   1234/sshd
```

Meaning:

- Port 22 open
    
- SSH service running
    
- Listening for connections
    

---

## 3. Show Only TCP Ports

```bash
netstat -tln
```

Used when checking:

- SSH
    
- HTTP
    
- HTTPS
    
- FTP
    

---

## 4. Show Only UDP Ports

```bash
netstat -uln
```

Used when checking:

- DNS
    
- DHCP
    
- NTP
    

---

## 5. Show Active Connections

```bash
netstat -an
```

Shows:

- Active connections
    
- Established sessions
    

---

## 6. Filter Specific Port

Example:

```bash
netstat -an | grep 80
```

Used to check:

- HTTP traffic
    
- Specific service
    

---

# Understanding Output

Example:

```
tcp   0   0   0.0.0.0:22   0.0.0.0:*   LISTEN
```

Breakdown:

|Section|Meaning|
|---|---|
|tcp|Protocol|
|0.0.0.0:22|Local address|
|LISTEN|Port open|

---

# TCP vs UDP in Netstat

## TCP

TCP shows:

- LISTEN
    
- ESTABLISHED
    
- CLOSE_WAIT
    

Example:

```
tcp   0   0   192.168.1.10:22   192.168.1.20:50000   ESTABLISHED
```

---

## UDP

UDP shows:

- No state
    
- Connectionless
    

Example:

```
udp   0   0   192.168.1.10:68   0.0.0.0:*
```

This is normal.

---

# Why Your IP Appears in UDP

Example:

```
udp  0  0  192.168.1.10:68
```

This usually means:

- DHCP communication
    
- IP assignment
    
- Router communication
    

Port 68 = DHCP client

This is **normal behavior**.

---

# Practical Lab

## Start SSH

```bash
sudo service ssh start
```

Check open port:

```bash
netstat -tuln
```

You should see:

```
0.0.0.0:22
```

---

## Start Python Web Server

```bash
python3 -m http.server 8080
```

Check again:

```bash
netstat -tuln
```

You should see:

```
0.0.0.0:8080
```

---

# Modern Alternative (Recommended)

Use `ss` instead of netstat

```bash
ss -tulnp
```

Why?

- Faster
    
- Modern
    
- More accurate
    

---

# Pentester Workflow

1. Start service
    
2. Check open ports
    
3. Identify services
    
4. Enumerate
    

---

# Common Ports to Watch

|Port|Service|
|---|---|
|21|FTP|
|22|SSH|
|23|Telnet|
|25|SMTP|
|53|DNS|
|80|HTTP|
|110|POP3|
|139|NetBIOS|
|443|HTTPS|
|445|SMB|
|3389|RDP|

---

# Quick Summary

- netstat shows open ports
    
- TCP = reliable connections
    
- UDP = fast connections
    
- Use `-tuln` for quick scan
    
- Use `-tulnp` for service names
    
- Use `ss` for modern alternative
    

---

# Must Remember

```bash
netstat -tuln
sudo netstat -tulnp
ss -tulnp
```