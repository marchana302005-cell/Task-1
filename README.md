
*Objective*
Discover open ports on devices within local network `192.168.31.72/24` to understand network exposure 

*Tools Used*
**Nmap**	7.95	Network discovery and TCP SYN port scanning
**Wireshark**	4.2.6	Packet capture analysis to validate scan behavior
**Command Prompt**	Windows 11	Execution environment


*Commands Used*
nmap -sS 192.168.31.0/24 -oN scan.txt



*Security Risks Identified*
Based on scan of 7 live hosts in `192.168.31.0/24`:

*Host: `DESKTOP-L0A2E6E.lan 192.168.31.72`*
Port	Service	Risk Level	
**3306/tcp**	MySQL	
**1521/tcp**	Oracle	tor
**135/tcp**	msrpc	*
**139/tcp**	netbios-ssn	
**8080/tcp**	http-proxy	
**49152/tcp**	unknown	*

*Learning Outcome*
1. *Technical Skill*: Executed TCP SYN scan using Nmap to enumerate 256 IPs. Identified 7 active hosts and 9 distinct open ports across the subnet.
2. *Analysis Skill*: Mapped raw port data to real-world threats like EternalBlue on port 445 and database exposure on 1521/3306. 

3. *Validation*: Used Wireshark to confirm SYN scan sends `SYN` packets and receives `RST,ACK` from closed ports, proving scan accuracy.

