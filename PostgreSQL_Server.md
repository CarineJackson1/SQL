# 🔐 Project Title: Secure PostgreSQL Server with Role-Based Access and Audit Logging

## 📌 Objective

This project demonstrates how to configure a PostgreSQL server with role-based access control and auditing using pgAudit. It simulates real-world scenarios of user access management and monitoring unauthorized activities.

## 🧰 Tools & Technologies Used
- Operating System: Ubuntu 22.04 LTS
- PostgreSQL 14
- pgAdmin (optional)
- pgAudit
- Nmap / Wireshark 
- Burp Suite / DVWA (for web-based SQLi projects)
- ELK Stack / Splunk (for logging)

## 🚀 Setup Instructions (Quick Start)
1. Clone the repo or follow the [setup.md](./setup.md) guide.
2. 
3. Install PostgreSQL:  
   ```bash
   sudo apt update
   sudo apt install postgresql postgresql-contrib

	3.	Create user roles:

CREATE ROLE analyst WITH LOGIN PASSWORD 'secure123';

	4.	[Continue with short setup instructions…]
	```

🧪 Key Features & Demonstrations
	•	✅ Role-based access control (GRANT/REVOKE)
	•	✅ Logging unauthorized access attempts
	•	✅ Real log analysis from PostgreSQL
	•	✅ Basic SQL injection test (if applicable)

📷 Screenshots

Step	Screenshot
PostgreSQL Audit Log	
Role Creation	
SQL Injection Attempt	

🧠 What I Learned
	•	Importance of least-privilege access to secure sensitive data
	•	How to log and monitor database activities with pgaudit
	•	How attackers exploit insecure SQL endpoints
	•	How to set up basic SIEM integration and alerting

🛡️ Security Best Practices Applied
	•	Principle of Least Privilege (PoLP)
	•	Encryption (if used)
	•	Log monitoring
	•	Role segregation
	•	Regular vulnerability scans
