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

**Phase 2: Configure ModSecurity**
sudo cp /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf
sudo sed -i 's/SecRuleEngine DetectionOnly/SecRuleEngine On/' /etc/modsecurity/modsecurity.conf

Phase 3: Integrate OWASP CRS
cd /etc/modsecurity
sudo git clone https://github.com/coreruleset/coreruleset.git
cd coreruleset
sudo cp crs-setup.conf.example crs-setup.conf

Restart Apache:

sudo systemctl restart apache2
sudo systemctl enable apache2

💣 Attack Simulation from Kali Linux
curl -A "sqlmap" http://<your-server-ip>

You should see logs in:
cat /var/log/apache2/modsec_audit.log

🔐 Optional Enhancements
	•	Add custom SecRule rules
	•	Integrate with ELK Stack for monitoring
	•	Setup Fail2Ban to block malicious IPs
	•	Containerize with Docker
	•	Build Python dashboard or alert system

