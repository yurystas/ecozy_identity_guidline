# 12. IT Security (source) (source2)

Backup process  
ISO 27001?

**Text:** eCozy is committed to protecting our infrastructure and user data by adhering to industry best practices.

* **Data in Transit:** All communication between our mobile/web clients and the backend, and between the backend and IoT devices, is encrypted using **TLS 1.2+**.  
* **Data at Rest:** Sensitive user data (e.g., passwords, API keys) stored in our database is encrypted using strong, modern hashing and encryption algorithms.  
* **Infrastructure:** Our AWS infrastructure is managed using **Infrastructure as Code (IaC)**. Access is restricted via IAM roles, multi-factor authentication (MFA) is mandatory for all admin accounts, and network access is limited by security groups and VPCs.  
* **Backup Process:** Our PostgreSQL database is backed up daily using automated AWS RDS snapshots, with point-in-time recovery (PITR) enabled. These backups are encrypted and stored in a separate, access-restricted S3 bucket.  
* **Compliance:** We conduct regular vulnerability scans and are working towards **ISO 27001** certification to formalize our Information Security Management System (ISMS).
