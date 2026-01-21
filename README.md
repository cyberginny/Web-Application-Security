# Web Application Security Assignment 3

**Date:** January 16-17, 2026  
**Course:** Web Application Security

[![Security](https://img.shields.io/badge/Security-Web%20Application-red)](https://github.com/cyberginny/Web-Application-Security)
[![Status](https://img.shields.io/badge/Status-Completed-success)](https://github.com/cyberginny/Web-Application-Security)
[![DVWA](https://img.shields.io/badge/DVWA-Tested-blue)](https://github.com/digininja/DVWA)
[![PrestaShop](https://img.shields.io/badge/PrestaShop-v9.0.2-orange)](https://www.prestashop.com)

---

## 📋 Executive Summary

This repository documents a comprehensive web application security assessment involving vulnerability exploitation, defensive implementation, and security hardening across multiple platforms.

### Assignment Components
1. **DVWA Attack Simulation** - SQL Injection and XSS exploitation
2. **ModSecurity WAF Configuration** - Web Application Firewall deployment and testing
3. **PrestaShop Security Assessment** - E-commerce platform hardening and vulnerability scanning

---

## 🎯 Key Findings

### DVWA Vulnerabilities Exploited

| Attack Type | Success Rate | Impact | CVSS Score |
|------------|--------------|--------|------------|
| SQL Injection (Basic) | ✅ 100% | Retrieved all 5 users | 9.8 (Critical) |
| SQL Injection (Advanced) | ✅ 100% | Extracted password hashes | 9.8 (Critical) |
| XSS (Reflected) | ✅ 100% | JavaScript execution | 7.1 (High) |
| XSS (Stored) | ✅ 100% | Session cookie theft | 7.1 (High) |

**Extracted Data:**
- 5 user accounts with MD5 password hashes
- Admin credentials: `admin:5f4dcc3b5aa765d61d8327deb882cf99` (password: "password")
- Session cookies via stored XSS payload

### ModSecurity WAF Effectiveness

| Metric | Result |
|--------|--------|
| SQL Injection Block Rate | **100%** |
| XSS Attack Block Rate | **100%** |
| False Positives | **0** |
| Response Time Impact | **< 200ms** |
| HTTP Response Code | **403 Forbidden** |

### PrestaShop Security Assessment

**Overall Risk Level:** 🟡 **MODERATE**

| Category | Status | Details |
|----------|--------|---------|
| Application Version | ✅ Good | v9.0.2 (up to date) |
| Default Accounts | ✅ Secured | Removed, 1 custom admin only |
| Demo Data | ✅ Cleared | All products, customers removed |
| Admin Directory | ✅ Renamed | `/admin` → `/admin-7f92xk` |
| HTTPS Enforcement | ❌ **HIGH RISK** | HTTP only - CVSS 7.4 |
| Security Headers | ⚠️ Missing | 5 headers not configured |
| Automated Backups | ✅ Configured | Daily at 4:00 AM |

**Vulnerabilities Found:** 6 Total
- 🔴 **Critical:** 0
- 🟠 **High:** 1 (Missing HTTPS)
- 🟡 **Medium:** 0
- 🟢 **Low:** 5 (Security headers)

---

## 📁 Repository Structure

```
web-security-assignment3/
├── README.md                          # This file - Project overview
├── docs/
│   ├── complete-report.md            # Full assignment report
│   ├── security-checklist.md         # PrestaShop security checklist
│   └── attack-simulation-report.md   # Detailed attack documentation
├── screenshots/
│   ├── dvwa/                         # DVWA attack evidence
│   │   ├── 01-sql-injection-basic.png
│   │   ├── 02-sql-injection-credentials.png
│   │   ├── 03-xss-reflected.png
│   │   ├── 04-xss-stored-payload.png
│   │   └── 05-xss-cookie-theft.png
│   ├── modsecurity/                  # WAF implementation evidence
│   │   ├── 06-modsecurity-installation.png
│   │   ├── 07-waf-rules-config.png
│   │   ├── 08-sql-injection-blocked.png
│   │   ├── 09-xss-blocked.png
│   │   ├── 10-audit-logs.png
│   │   └── 11-waf-testing-script.png
│   └── prestashop/                   # PrestaShop security evidence
│       ├── 12-system-information.png
│       ├── 13-module-manager.png
│       ├── 14-employees.png
│       ├── 15-products-cleared.png
│       ├── 16-customers-cleared.png
│       ├── 17-orders-canceled.png
│       ├── 18-security-settings.png
│       └── 19-admin-directory-renamed.png
└── scripts/
    ├── backup.sh                     # PrestaShop backup automation
    ├── waf_test.sh                   # ModSecurity testing script
    ├── prestashop_scanner.py         # Custom vulnerability scanner
    └── custom-dvwa-rules.conf        # ModSecurity WAF rules
```

---

## 🔒 Security Implementations

### 1. DVWA Protection (ModSecurity)

**Custom WAF Rules Deployed:**

```apache
# SQL Injection Protection (Rule ID: 1001)
SecRule ARGS "@rx (?i:(\s*(union|select|insert|update|delete)\s+))" \
  "id:1001,phase:2,block,msg:'SQL Injection Detected'"

# XSS Protection (Rule ID: 2001)
SecRule ARGS "@rx (?i:<script[^>]*>)" \
  "id:2001,phase:2,block,msg:'XSS Attack Detected'"
```

**Results:**
- ✅ All SQL injection attempts blocked (HTTP 403)
- ✅ All XSS payloads intercepted
- ✅ Legitimate traffic allowed (200 OK)
- ✅ ModSecurity v2.6.12 running in "ENABLED" mode

### 2. PrestaShop Hardening Checklist

| Security Measure | Status | Implementation |
|------------------|--------|----------------|
| Admin Directory Renamed | ✅ | `/admin-7f92xk` |
| Default Accounts Removed | ✅ | Only 1 custom admin |
| Demo Data Cleared | ✅ | 0 products, 0 customers |
| Install Directory Removed | ✅ | Verified deleted |
| File Permissions | ✅ | 755 (dirs), 644 (files) |
| Password Policy | ✅ | Score 3 (Safely unguessable) |
| Automated Backups | ✅ | Daily cron job |
| Debug Mode | ✅ | Disabled |
| HTTPS Enforcement | ❌ | **Pending** |
| Security Headers | ❌ | **Pending** |

---

## 🛠️ Tools & Environment

### Lab Setup

**Operating System:**
- Kali Linux 6.18.3-1kali2 (Debian)

**Target Applications:**
- DVWA (Latest - Docker)
- PrestaShop v9.0.2
- Apache 2.4.65/2.4.66 (Debian)
- MySQL 8.0
- PHP 8.4.15

**Security Tools:**
- ModSecurity v2.6.12 (Web Application Firewall)
- Custom Python Vulnerability Scanner
- Docker & Docker Compose
- Git & GitHub

**Attack Tools:**
- Manual SQL Injection techniques
- Custom XSS payloads
- cURL for WAF testing

---

## 📊 Detailed Reports

### Part 1: DVWA Attack Simulation

**SQL Injection Results:**
- ✅ Successfully bypassed authentication using `1' OR '1'='1`
- ✅ Extracted 5 user accounts using UNION-based injection
- ✅ Retrieved MD5 password hashes for all users
- 📝 [View Complete Report](docs/complete-report.md#part-1-dvwa-attack-simulation)

**XSS Attack Results:**
- ✅ Reflected XSS: Executed `<script>alert('XSS')</script>`
- ✅ Stored XSS: Injected cookie-stealing payload in guestbook
- ✅ Captured session cookie: `PHPSESSID=20214f69ee8ff1989d98e9fdd68c5f8`
- 📝 [View Screenshots](screenshots/dvwa/)

### Part 2: ModSecurity WAF Configuration

**Implementation:**
- ✅ Installed ModSecurity via apt package manager
- ✅ Configured custom rules for SQL injection and XSS
- ✅ Tested with automated script: 100% block rate
- ✅ Verified legitimate traffic passes through
- 📝 [View WAF Configuration](scripts/custom-dvwa-rules.conf)

### Part 3: PrestaShop Security Assessment

**Reconnaissance:**
- Custom Python scanner identified 6 vulnerabilities
- Admin panel not found at default locations ✅
- Version disclosure: None found ✅

**Vulnerabilities Identified:**
1. 🔴 **HIGH:** Missing HTTPS enforcement (CVSS 7.4)
2. 🟢 **LOW:** Missing X-Frame-Options header
3. 🟢 **LOW:** Missing X-Content-Type-Options header
4. 🟢 **LOW:** Missing Strict-Transport-Security header
5. 🟢 **LOW:** Missing Content-Security-Policy header
6. 🟢 **LOW:** Missing X-XSS-Protection header

**Hardening Applied:**
- ✅ Removed default "John Doe" admin account
- ✅ Deleted all demo products and customers
- ✅ Canceled 5 sample orders
- ✅ Renamed admin directory to obscure path
- ✅ Configured automated daily backups
- ✅ Set proper file permissions (755/644)

📝 [View Security Checklist](docs/security-checklist.md)

---

## 🚀 Quick Start

### Clone Repository

```bash
git clone https://github.com/cyberginny/Web-Application-Security.git
cd Web-Application-Security
```

### View Documentation

```bash
# Read complete report
cat docs/complete-report.md

# Check security checklist
cat docs/security-checklist.md

# View attack simulation details
cat docs/attack-simulation-report.md
```

### Run PrestaShop Scanner

```bash
cd scripts
python3 prestashop_scanner.py http://target-url
```

### Test ModSecurity WAF

```bash
cd scripts
chmod +x waf_test.sh
./waf_test.sh http://localhost:8080
```

### View Backup Configuration

```bash
cd scripts
cat backup.sh

# Check backup files
ls -lh /opt/prestashop-backups/
```

---

## 📸 Evidence Gallery

### DVWA Exploitation

| Attack | Screenshot | Result |
|--------|------------|--------|
| SQL Injection (Basic) | ![SQL Basic](screenshots/dvwa/01-sql-injection-basic.png) | All 5 users displayed |
| SQL Injection (Advanced) | ![SQL Advanced](screenshots/dvwa/02-sql-injection-credentials.png) | Password hashes extracted |
| XSS (Reflected) | ![XSS Reflected](screenshots/dvwa/03-xss-reflected.png) | Alert box displayed |
| XSS (Stored) | ![XSS Stored](screenshots/dvwa/04-xss-stored-payload.png) | Payload stored in guestbook |
| Session Hijacking | ![Cookie Theft](screenshots/dvwa/05-xss-cookie-theft.png) | PHPSESSID captured |

### ModSecurity WAF

| Test | Screenshot | Result |
|------|------------|--------|
| Installation | ![Install](screenshots/modsecurity/06-modsecurity-installation.png) | Engine mode: ENABLED |
| WAF Rules | ![Rules](screenshots/modsecurity/07-waf-rules-config.png) | Custom rules loaded |
| SQL Blocked | ![SQL Block](screenshots/modsecurity/08-sql-injection-blocked.png) | HTTP 403 Forbidden |
| XSS Blocked | ![XSS Block](screenshots/modsecurity/09-xss-blocked.png) | HTTP 403 Forbidden |
| Audit Logs | ![Logs](screenshots/modsecurity/10-audit-logs.png) | All attacks logged |

### PrestaShop Security

| Component | Screenshot | Status |
|-----------|------------|--------|
| System Info | ![System](screenshots/prestashop/12-system-information.png) | v9.0.2 |
| Employees | ![Employees](screenshots/prestashop/14-employees.png) | 1 custom admin only |
| Products | ![Products](screenshots/prestashop/15-products-cleared.png) | 0 products (cleared) |
| Customers | ![Customers](screenshots/prestashop/16-customers-cleared.png) | 0 customers |
| Orders | ![Orders](screenshots/prestashop/17-orders-canceled.png) | 5 canceled |
| Security | ![Security](screenshots/prestashop/18-security-settings.png) | Score 3 policy |

---

## 📈 Risk Assessment Summary

### Vulnerability Distribution

```
Critical: ███████████████████░░░░░░░░░  0 (0%)
High:     ███████████████████████░░░░░  1 (16.7%)
Medium:   ░░░░░░░░░░░░░░░░░░░░░░░░░░░░  0 (0%)
Low:      ████████████████████████████  5 (83.3%)
```

### Risk Matrix

| Threat | Likelihood | Impact | Risk Level | CVSS Score |
|--------|-----------|--------|------------|------------|
| DVWA SQL Injection | High | Critical | 🔴 Critical | 9.8 |
| DVWA XSS | High | High | 🟠 High | 7.1 |
| PrestaShop Missing HTTPS | High | High | 🟠 High | 7.4 |
| Missing Security Headers | High | Low | 🟢 Low | 3.1 |
| Admin Brute Force | Medium | Medium | 🟡 Medium | 3.5 |

### Overall Security Posture

**Before Hardening:** 🔴 **Critical** (Multiple high-severity vulnerabilities)

**After Hardening:** 🟡 **Moderate** (1 HIGH, 5 LOW vulnerabilities remaining)

**Risk Reduction:** ~70% attack surface reduced

---

## 🎓 Learning Outcomes

### Skills Demonstrated

1. **Offensive Security:**
   - SQL Injection exploitation (basic and advanced)
   - Cross-Site Scripting (reflected and stored)
   - Session hijacking techniques
   - Database enumeration

2. **Defensive Security:**
   - Web Application Firewall deployment
   - Custom WAF rule creation
   - Security hardening procedures
   - Vulnerability assessment

3. **Security Tools:**
   - ModSecurity configuration
   - Custom Python scanner development
   - Bash scripting for automation
   - Docker containerization

4. **Documentation:**
   - Professional security reporting
   - Evidence collection and presentation
   - Risk assessment and prioritization

---

## ⚠️ Disclaimer

**IMPORTANT:** This repository is for **educational purposes only**.

- All attacks were performed in a **controlled lab environment**
- No unauthorized systems were accessed
- All vulnerabilities were responsibly disclosed
- This work is submitted as academic coursework

**Legal Notice:**
Unauthorized access to computer systems is illegal under:
- Computer Fraud and Abuse Act (CFAA) - USA
- Computer Misuse Act - UK
- Similar laws in other jurisdictions

**Always obtain proper authorization before conducting security testing.**

---

## 🔗 References & Resources

### Documentation
- [OWASP Top 10 2021](https://owasp.org/Top10/)
- [ModSecurity Reference Manual](https://github.com/SpiderLabs/ModSecurity/wiki)
- [PrestaShop Security Guide](https://devdocs.prestashop.com/8/basics/security/)
- [DVWA Documentation](https://github.com/digininja/DVWA)

### Tools
- [OWASP ZAP](https://www.zaproxy.org/)
- [Burp Suite](https://portswigger.net/burp)
- [SQLMap](http://sqlmap.org/)
- [Nikto](https://github.com/sullo/nikto)

### Standards
- [OWASP Core Rule Set (CRS)](https://coreruleset.org/)
- [CWE/SANS Top 25](https://cwe.mitre.org/top25/)
- [CVSS Calculator](https://www.first.org/cvss/calculator/3.1)

---

## 📞 Contact

**Student:** Paul Deborah Ginikachi  
**GitHub:** [@cyberginny](https://github.com/cyberginny)  
**Email:** ginikapaul67@gmail.com

---

## 📄 License

This project is submitted as academic work for the Web Application Security course.

**Academic Integrity Notice:** This work represents original research and documentation completed by the student listed above.

---

## 🏆 Acknowledgments

- **DVWA Team** - For providing the vulnerable web application training platform
- **ModSecurity Team** - For the open-source Web Application Firewall
- **PrestaShop Community** - For the e-commerce platform
- **Kali Linux Team** - For the security testing distribution
- **Course Instructor** - For guidance and assignment design

---

**Last Updated:** January 17, 2026  
**Repository Status:** ✅ Complete - Final Submission  
**Version:** 1.0.0

---

<div align="center">

**⭐ If this helped you, please star this repository! ⭐**

Made with 🔒 by Paul Deborah Ginikachi

</div>
