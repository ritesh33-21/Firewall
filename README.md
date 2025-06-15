# apache-waf-setup-guide
# 🛡️ Web Application Firewall (WAF) Project: ModSecurity + OWASP CRS

This project demonstrates how to configure a **Web Application Firewall (WAF)** using **ModSecurity** with **Apache2** on **Ubuntu**, and test it using offensive security tools from **Kali Linux**.

---

## 🧰 Tools & Technologies

| Component         | Tool/Technology              |
|------------------|------------------------------|
| OS (Deployment)  | Ubuntu 20.04 or higher       |
| WAF Engine       | ModSecurity (Apache module)  |
| Web Server       | Apache2                      |
| Ruleset          | OWASP Core Rule Set (CRS)    |
| Attacker OS      | Kali Linux                   |
| Tools            | sqlmap, XSSer, Nikto, curl   |

---

## 🛠️ Setup Guide

### Phase 1: Install Apache & ModSecurity

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y apache2 libapache2-mod-security2 git curl
sudo a2enmod security2
