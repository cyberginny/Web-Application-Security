# Web-Application-Security
Complete security assessment covering DVWA exploitation (SQL Injection &amp; XSS), ModSecurity WAF implementation, and PrestaShop hardening with vulnerability scanning

# Web Application Security   
**Date:** January 16-17, 2026  
**Course:** Web Application Security

## 📋 Overview

This repository contains documentation and evidence for Assignment 3: Attack and Defend Web Application Security Assessment.

### Objectives Completed
- ✅ SQL Injection attacks on DVWA
- ✅ XSS (Cross-Site Scripting) attacks on DVWA
- ✅ ModSecurity WAF configuration and testing
- ✅ PrestaShop security assessment and hardening
- ✅ Attack simulation on PrestaShop

## 🎯 Key Findings

### DVWA Vulnerabilities
- **SQL Injection:** Successfully extracted 5 user accounts with MD5 password hashes
- **XSS Attacks:** Both reflected and stored XSS vulnerabilities exploited
- **Impact:** Critical - Full database compromise possible

### WAF Effectiveness
- **ModSecurity:** 100% block rate for SQL injection and XSS attacks
- **False Positives:** 0
- **Performance:** Response times < 200ms

### PrestaShop Security
- **Risk Level:** Moderate
- **Critical Issue:** Missing HTTPS enforcement (CVSS 7.4)
- **Vulnerabilities Found:** 1 HIGH, 5 LOW
- **Hardening Applied:** Admin directory renamed, demo data cleared, backups configured

## 📁 Repository Structure
web-security-assignment3/
├── docs/               # Complete documentation
├── screenshots/        # Visual evidence
├── scripts/           # Security tools and configs
└── README.md          # This file

## 🔒 Security Implementations

### DVWA Protection (ModSecurity)
- SQL Injection blocking rules (ID: 1001)
- XSS protection rules (ID: 2001)
- Custom rules for DVWA-specific attacks

### PrestaShop Hardening
- ✅ Default accounts removed
- ✅ Demo data cleared
- ✅ Admin directory renamed to `admin-7f92xk`
- ✅ Automated daily backups
- ✅ File permissions secured (755/644)
- ⚠️ HTTPS implementation pending

## 📊 Vulnerability Summary

| Vulnerability | Severity | Status | CVSS Score |
|--------------|----------|--------|------------|
| DVWA SQL Injection | Critical | Mitigated | 9.8 |
| DVWA XSS | High | Mitigated | 7.1 |
| PrestaShop Missing HTTPS | High | Identified | 7.4 |
| Missing Security Headers | Low | Identified | 3.1 |

## 🛠️ Tools Used

- **DVWA:** Damn Vulnerable Web Application
- **ModSecurity:** v2.6.12 Web Application Firewall
- **PrestaShop:** v9.0.2 E-commerce Platform
- **Kali Linux:** Security testing OS
- **Docker:** Containerization
- **Custom Scanner:** Python vulnerability scanner

## 📝 Documentation

- [Complete Report](docs/complete-report.md)
- [Security Checklist](docs/security-checklist.md)
- [Attack Simulation Report](docs/attack-simulation-report.md)

## 🚀 Quick Start

## 🔒 Security Implementations

### DVWA Protection (ModSecurity)
- SQL Injection blocking rules (ID: 1001)
- XSS protection rules (ID: 2001)
- Custom rules for DVWA-specific attacks

### PrestaShop Hardening
- ✅ Default accounts removed
- ✅ Demo data cleared
- ✅ Admin directory renamed to `admin-7f92xk`
- ✅ Automated daily backups
- ✅ File permissions secured (755/644)
- ⚠️ HTTPS implementation pending

## 📊 Vulnerability Summary

| Vulnerability | Severity | Status | CVSS Score |
|--------------|----------|--------|------------|
| DVWA SQL Injection | Critical | Mitigated | 9.8 |
| DVWA XSS | High | Mitigated | 7.1 |
| PrestaShop Missing HTTPS | High | Identified | 7.4 |
| Missing Security Headers | Low | Identified | 3.1 |

## 🛠️ Tools Used

- **DVWA:** Damn Vulnerable Web Application
- **ModSecurity:** v2.6.12 Web Application Firewall
- **PrestaShop:** v9.0.2 E-commerce Platform
- **Kali Linux:** Security testing OS
- **Docker:** Containerization
- **Custom Scanner:** Python vulnerability scanner

## 📝 Documentation

- [Complete Report](docs/complete-report.md)
- [Security Checklist](docs/security-checklist.md)
- [Attack Simulation Report](docs/attack-simulation-report.md)

## 🚀 Quick Start

### Clone Repository
```bash
git clone https://github.com/yourusername/web-security-assignment3.git
cd web-security-assignment3
```

### Run Security Scanner
```bash
cd scripts
python3 prestashop_scanner.py http://target-url
```

### Run Security Scanner
```bash
cd scripts
python3 prestashop_scanner.py http://target-url
```

## ⚠️ Disclaimer

This repository is for educational purposes only. The techniques demonstrated should only be used in authorized testing environments. Unauthorized access to computer systems is illegal.

## 📄 License

This project is submitted as academic work for Web Application Security course.

---

**Note:** Sensitive information (passwords, API keys) has been removed or redacted from all files in this repository.
