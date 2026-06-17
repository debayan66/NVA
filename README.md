# Network-Vulnerability-Assessment

Network & Web Application Vulnerability Assessment and Security Audit

## Project Overview

This project demonstrates a complete vulnerability assessment workflow in a controlled lab environment. The objective was to simulate a real-world security assessment by discovering network assets, identifying exposed services, detecting vulnerabilities, analyzing network traffic, and documenting remediation strategies.

The assessment was performed using Kali Linux as the attacker/security testing machine against intentionally vulnerable systems such as Metasploitable and OWASP vulnerable applications.

The project focuses on understanding the complete vulnerability management lifecycle:

* Reconnaissance
* Network scanning
* Service enumeration
* Vulnerability identification
* Web application testing
* Traffic analysis
* Security reporting

---

# Lab Environment

## Attacker Machine

**Operating System:**

* Kali Linux

**Platform:**

* Oracle VirtualBox

Tools Used:

* Nmap
* Nikto
* Burp Suite Community Edition
* Wireshark

## Target Machines

Intentionally vulnerable environments:

* Metasploitable Linux VM
* OWASP Vulnerable Web Applications

Network Configuration:


Kali Linux
     |
Host-Only Network
     |
Vulnerable Target VM


The lab was isolated from external networks to safely perform testing.

---

# Tools and Purpose

## 1. Nmap - Network Enumeration

Nmap was used for:

* Host discovery
* Open port detection
* Service enumeration
* Operating system fingerprinting
* Vulnerability script scanning

Example scans:

bash
nmap -sn <network-range>

nmap -sV -sC -O <target-ip>

nmap --script vuln <target-ip>


Information gathered:

* Active hosts
* Running services
* Service versions
* Possible vulnerabilities

---

# 2. Nikto - Web Server Vulnerability Assessment

Nikto was used to analyze web services running on the target machine.

Testing included:

* Server misconfiguration detection
* Dangerous files
* Outdated components
* Missing security headers

Example:

bash
nikto -h http://target-ip


Findings analyzed:

* Information disclosure
* Directory indexing
* HTTP security weaknesses

---

# 3. Burp Suite - Web Application Security Testing

Burp Suite was used for manual web application testing.

Assessment areas:

## SQL Injection Testing

Checked whether user input was properly validated.

Impact:

* Unauthorized database access
* Data leakage

Mitigation:

* Prepared SQL statements
* Input validation

---

## Cross Site Scripting (XSS)

Tested input fields for script injection.

Impact:

* Client-side attacks
* Session compromise

Mitigation:

* Output encoding
* Input sanitization

---

## Authentication Security Testing

Analyzed:

* Login mechanisms
* Weak authentication controls
* Request manipulation

---

# 4. Wireshark - Network Traffic Analysis

Wireshark was used for packet inspection and network monitoring.

Analysis performed:

* Packet capture
* Protocol inspection
* Plain-text communication detection

Example security issue:

Telnet communication exposes credentials because data is transmitted without encryption.

Recommendation:

Replace insecure protocols with secure alternatives:

* SSH instead of Telnet
* HTTPS instead of HTTP

---

# Assessment Methodology

The following security testing methodology was followed:


Information Gathering

        ↓

Network Scanning

        ↓

Service Enumeration

        ↓

Vulnerability Detection

        ↓

Manual Verification

        ↓

Risk Classification

        ↓

Reporting & Recommendations


---

# Sample Security Findings

| Vulnerability                 | Severity | Tool Used      |
| ----------------------------- | -------- | -------------- |
| Insecure Telnet Service       | High     | Nmap/Wireshark |
| Outdated Services             | High     | Nmap           |
| Missing HTTP Security Headers | Medium   | Nikto          |
| Web Input Vulnerabilities     | High     | Burp Suite     |
| Information Disclosure        | Medium   | Nikto          |

---

# Challenges Faced During Implementation

## OpenVAS / Greenbone Community Edition Issue

Initially, Greenbone Vulnerability Manager (OpenVAS) was planned as the primary automated vulnerability scanner.

However, multiple issues were encountered:

* High resource consumption inside VirtualBox environment
* Database initialization failures
* PostgreSQL service issues
* Feed synchronization problems
* Long scan processing times on limited VM resources

Instead of relying completely on automated scanning, the methodology was redesigned using lightweight and manual security tools:

* Nmap NSE vulnerability scripts
* Nikto web assessment
* Burp Suite manual testing
* Wireshark traffic analysis

This approach provided deeper understanding of vulnerability discovery instead of depending only on automated scanner reports.

---

# Key Learnings

Through this project, practical experience was gained in:

* Linux security environment setup
* Network reconnaissance
* Vulnerability assessment workflow
* Web application security testing
* Packet analysis
* CVE research
* Security documentation

---

# Future Improvements

Planned enhancements:

## Add Automated Vulnerability Scanning

Integrate:

* Greenbone/OpenVAS after resolving VM resource limitations

## Add Exploitation Verification

Include controlled vulnerability validation using:

* Metasploit Framework

## Add More Vulnerable Environments

Future targets:

* DVWA
* OWASP Juice Shop

## Create Security Dashboard

Develop a dashboard showing:

* Vulnerability statistics
* Risk levels
* Scan history

## Add Remediation Validation

Perform:

Initial Scan → Apply Fix → Rescan

to demonstrate complete vulnerability management.

---

# Disclaimer

This project was performed only in a controlled lab environment using intentionally vulnerable machines.

The techniques demonstrated are strictly for cybersecurity learning, ethical hacking practice, and defensive security improvement.

Unauthorized testing against systems without permission is illegal.

---

# Skills Demonstrated

* Vulnerability Assessment
* Penetration Testing Methodology
* Network Security
* Linux Security
* Web Application Testing
* Security Analysis
* Technical Reporting
* Risk Assessment
