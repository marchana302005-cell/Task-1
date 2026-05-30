# Task 1: Network Port Scanning & Risk Assessment

## 1. Objective
Conduct authorized reconnaissance on local subnet `192.168.31.0/24` to identify network assets and open ports per **ISO/IEC 27001:2022 Annex A 12.6.1 – Management of Technical Vulnerabilities**.

## 2. Scan Details
| Parameter | Value |
| --- | --- |
| **Command** | `nmap -sS 192.168.31.0/24` |
| **Date** | 30 September 2026 |
| **Hosts Up** | 7 of 256 IPs scanned |
| **Duration** | 49.92 seconds |
| **Scanner** | Nmap 7.95 on Windows 11 |

## 3. Key Findings – High Risk Host
**Host**: `DESKTOP-L0A2E6E.lan (192.168.31.72)`  
**MAC**: `42:46:C8:9A:9A:9D`

| Port | State | Service | GRC Risk Rating | ISO 27001 Control |
| --- | --- | --- | --- | --- |
| 135/tcp | open | msrpc | **Medium** – RPC endpoint mapper | A.8.1.1 Asset Inventory |
| 139/tcp | open | netbios-ssn | **Medium** – Legacy file sharing | A.13.1.1 Network Controls |
| 445/tcp | open | microsoft-ds | **CRITICAL** – SMB, EternalBlue/WannaCry vector | A.12.6.1 Vulnerability Mgmt |
| 1521/tcp | open | oracle | **High** – Database exposed to LAN | A.9.1.2 Access to Networks |
| 3306/tcp | open | mysql | **High** – Default DB port, brute-force risk | A.12.4.1 Event Logging |
| 8080/tcp | open | http-proxy | **Medium** – Unencrypted admin interface | A.13.2.1 Information Transfer |

**Other Hosts**: 
- `192.168.31.199`: Ports 49152, 62078 `iphone-sync` open
- `realme-P1-5G.lan (192.168.31.182)`: Port 7 `echo` filtered
- `OnePlus-Nord2-5G.lan`, `chuangmi_camera_026c05.lan`: All 1000 ports closed

## 4. GRC & Legal Compliance Mapping
| Framework | Clause | Evidence from This Scan |
| --- | --- | --- |
| **ISO 27001:2022** | A.12.6.1 | Identified unpatched SMB port 445 for remediation tracking |
| **ISO 27001:2022** | A.8.1.1 | Inventory of 7 active network assets with MAC addresses |
| **IT Act 2000** | Sec 43A | Due diligence via proactive scanning of personal network |
| **CERT-In Advisory** | CIVN-2017-0001 | Port 445 flagged as critical per WannaCry advisory |

## 5. Remediation Priority
1. **IMMEDIATE**: Disable SMBv1 on `192.168.31.72`. Apply patch MS17-010. Port 445 must be blocked at firewall per A.13.1.1.
2. **HIGH**: Change MySQL 3306 to bind `127.0.0.1` only. Remove from LAN exposure.
3. **MEDIUM**: Restrict Oracle 1521 access via Windows Firewall rules.

## 6. Legal Disclaimer
Scan performed only on personally owned devices within private RFC 1918 range `192.168.31.0/24`. No external/public infrastructure was tested. Compliant with **IT Act 2000 Section 43 & 66**.

## 7. Evidence Files
- `nmap -sS 192.168.31.7224.txt`: Raw scan output
- `wireshark.jpeg`: Packet capture validating SYN scan
- `192.168.31.72.jpeg`: Target host identification
