# 🔍 Task 1: Basic Network Scanning with Nmap

## Objective
The primary objective of this task was to perform basic network reconnaissance on a target machine to identify open ports, the services running on those ports, and the corresponding version information.

## Target Information
* **Target:** Local/Test VM (Specify the target if applicable, e.g., 'Target VM running Ubuntu')
* **Target IP Address:** `[Insert Target IP Address Here, e.g., 192.168.1.50]`
* **Scan Date:** [Insert Date Here, e.g., December 14, 2025]

## Tools and Methodology
| Tool Used | Command Syntax | Description |
| :--- | :--- | :--- |
| **Nmap** (Network Mapper) | `sudo nmap -sS -sV -p- [Target IP]` | Used the **SYN Stealth Scan** (`-sS`) for fast port identification and the **Service Version Detection** (`-sV`) to confirm the software running on the open ports. The `-p-` flag scanned all 65535 ports. |

## Scan Results Summary

The scan revealed **[Number]** open ports on the target machine. The key findings are summarized in the table below:

| Port/Protocol | Service Identified | Version | Security Significance |
| :---: | :--- | :--- | :--- |
| **22/tcp** | ssh | OpenSSH [Version] | **Secure Management:** Necessary for remote administration. Must be secured with strong credentials, MFA, and possibly restricted IP access. |
| **80/tcp** | http | Apache httpd [Version] | **Web Server:** Indicates a web application is running. Vulnerable to unencrypted data transmission and web application attacks (e.g., XSS, injection). |
| **443/tcp** | https | Apache httpd [Version] | **Secure Web Server:** Indicates encrypted web traffic (SSL/TLS). Important to ensure a strong, current TLS protocol is in use. |
| **3389/tcp** | ms-wbt-server | Microsoft RDP [Version] | **Remote Desktop Protocol:** Often a target for brute-force attacks. Should be restricted or protected by a VPN/gateway. |
| **[Other Port]** | [Other Service] | [Version] | [Explain significance] |

***Note:** The full, raw output of the Nmap scan is available in the `nmap_scan_results.txt` file.*

## Analysis and Significance of Open Ports

Each open port represents a potential entry point into the system. Identifying the service and version running is the crucial first step of a vulnerability assessment.

* **SSH (Port 22):** Its presence is standard for Linux servers but requires vigilance. Outdated versions may contain known vulnerabilities.
* **HTTP/HTTPS (Ports 80/443):** These ports confirm the target is hosting web content. If no web service is intended, these ports should be blocked at the firewall level. For an exposed server, the security of the web application itself becomes paramount.
* **Version Identification:** The `-sV` output provides the specific version number. This allows a security analyst to cross-reference the software (e.g., Apache httpd 2.4.41) against public vulnerability databases (like CVE) to identify existing risks.

