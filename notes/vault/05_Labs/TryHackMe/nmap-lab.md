## Xmas Scan Attempt

I attempted an Xmas scan using:

nmap -sX -p1-9999 10.113.148.90

I initially encountered a syntax error.

Screenshot:

![[screenshots/nmap-xmas-scan-error-and-fix.png]]

After correcting the command:

nmap -sX -p1-999 10.113.148.90

The scan completed successfully.

### Lessons Learned

- Pay attention to syntax
- Verify port range formatting
- Use verbose output (-vv) for debugging