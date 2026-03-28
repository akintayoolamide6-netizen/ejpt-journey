# NSE Scripts — My Personal Notes (Enumeration Phase)

After running my port scans and identifying open services, I moved into **enumeration** using **NSE scripts**.

This is where things started getting more interesting.

---

# What Are NSE Scripts?

**NSE** means **Nmap Scripting Engine**.

These are **built-in scripts inside Nmap** that help me:

- Gather more information
    
- Enumerate services
    
- Find vulnerabilities
    
- Discover users, shares, and configs
    

Instead of just seeing **open ports**, NSE scripts help me **dig deeper**.

So instead of:

"I see SMB is open"

I now ask:

- What shares exist?
    
- What users exist?
    
- What OS is running?
    

This is enumeration.

---

# My First NSE Script — Default Script Scan

I ran:

```bash
nmap -sC 192.168.246.131
```

What `-sC` does:

- Runs **default scripts**
    
- Automatically checks common services
    
- Quick enumeration
    

This helped me:

- Gather more information automatically
    
- Save time
    
- Get quick insights
    

This is usually my **first enumeration step**.

---

# SMB Enumeration (My Practical Step)

From my earlier scan, I saw:

- 139 open
    
- 445 open
    

So I knew **SMB was running**.

Then I tried:

```bash
nmap --script=smb-enum-shares 192.168.246.131
```

At first, I made a mistake.

I typed:

```bash
nmap --script=smb-enu-share 192.168.246.131
```

This gave me an **error**.

Then I noticed:

- I misspelled **enum**
    
- I corrected it
    

Then I ran:

```bash
nmap --script=smb-enum-shares 192.168.246.131
```

Now it worked.

This script tries to:

- Find shared folders
    
- Find accessible shares
    
- Discover public directories
    

This helps me identify:

- Sensitive files
    
- Misconfigured shares
    
- Anonymous access
    

---

# Other Scripts I Tried

## SMB OS Discovery

I ran:

```bash
nmap --script=smb-os-discovery 192.168.246.131
```

This helps me find:

- Operating system
    
- Hostname
    
- Workgroup
    
- Domain
    

This is useful for:

- Identifying the target
    
- Planning next attack
    

---

## SMB User Enumeration

I tried:

```bash
nmap --script=smb-enum-users 192.168.246.131
```

This script tries to:

- Find usernames
    
- Enumerate accounts
    
- Identify valid users
    

This is useful because:

- Usernames help with brute force attacks
    
- Usernames help with login attempts
    

---

# My Thought Process (What I Was Looking For)

When I ran these scripts, I was looking for:

- Shared folders
    
- Usernames
    
- OS information
    
- Misconfigurations
    

This helped me move from:

**Scanning → Enumeration**

Which is the real next step in penetration testing.

---

# My Workflow Now

1. Port Scan
    

```bash
nmap -sV 192.168.246.131
```

2. Identify services
    

Example:

- FTP
    
- SSH
    
- SMB
    
- HTTP
    

3. Run NSE Scripts
    

```bash
nmap -sC 192.168.246.131
```

4. Target specific services
    

```bash
nmap --script=smb-enum-shares 192.168.246.131
```

---

# My Key Learning

- NSE scripts help me gather deeper info
    
- Always check open services first
    
- Then run relevant scripts
    
- Spelling matters (I learned this quickly)
    
- Enumeration is where real pentesting starts
    

---

# My Personal Reminder