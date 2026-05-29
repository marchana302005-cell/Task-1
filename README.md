Cybersecurity-Task1
Objective
To discover open ports on devices in the local network and understand network exposure using Nmap.

Tools Used
Nmap 7.99
Windows Command Prompt
Network Information
IPv4 Address: 192.168.31.72
Network Range: 192.168.31.72/24
Commands Used
nmap -sS 192.168.31.72/24
nmap -sS 192.168.31.72/24 -oN scan_results.txt

Results
Scanned 256 IP addresses.

Found 9 active hosts.

Identified multiple open ports on network devices.

Open ports on local desktop included:

135 MSRPC
139 NetBIOS-ssn
445 Microsoft-DS
2869 ICSLAP
3306 MySQL
55555 Unknown

Security Risks
Open ports can expose network services to attackers.
SMB-related ports (139 and 445) should be monitored carefully.
Database services such as MySQL should be protected using strong authentication.
Firewalls should be configured to restrict unnecessary access.

Outcome
know network reconnaissance.
Performed TCP SYN scanning using Nmap.
Identified active hosts and open ports.
Understood network exposure and security implications.
