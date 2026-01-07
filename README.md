# azure-secure-web-lab
Secure Azure web application lab demonstrating network security, monitoring, and alerting


## Overview
This project demonstrates the deployment of a **secure web application on Microsoft Azure**, focusing on **network security, access control, monitoring, and cost-aware cloud operations**.  
The lab simulates a real-world scenario where a publicly accessible web application is protected using least-privilege network controls and monitored using Azure-native security and observability services.

---

## Architecture Summary
The solution is deployed within a **single Azure resource group** to simplify lifecycle management, access control, and cost tracking.

**High-level components:**
- Azure Virtual Network with subnet isolation
- Network Security Group enforcing least-privilege access
- Ubuntu Virtual Machine hosting an NGINX web application
- Secure SSH access using key-based authentication
- Centralized logging with Log Analytics
- Metric-based alerting using Azure Monitor

📌 *See the architecture diagram below

<img width="481" height="711" alt="Azure Secure Web Application Lab Diagram drawio" src="https://github.com/user-attachments/assets/4c7ff632-b255-48bd-92f2-3f85886ed322" />



---

## Deployed Resources

### Resource Group
- **Name:** `rg-azure-secure-web-lab`
- <img width="1407" height="404" alt="rg-azure-secure-web" src="https://github.com/user-attachments/assets/d2741e95-5c7f-4326-9c40-7f3b984ea0a4" />


### Networking
- **Virtual Network:** `vnet-secure-web` (10.0.0.0/16)
- **Subnet:** `default` (10.0.0.0/24)
- **Network Security Group:** `nsg-web-subnet`
  - Allow HTTP (80) from Internet
  - Allow SSH (22) from administrator IP only
  - Deny all other inbound traffic
  - <img width="1289" height="481" alt="nsg-web-subnet" src="https://github.com/user-attachments/assets/fa7b8434-4ccc-4157-a32f-b22c77064ed8" />

- **Public IP:** `vm-web03-ip`
- <img width="850" height="643" alt="vm-web03-ip" src="https://github.com/user-attachments/assets/00c084b9-2dcf-4412-b9f8-ffefebad16de" />


### Compute
- **Virtual Machine:** `vm-web03`
- 
- **OS:** Ubuntu Server
- **Web Server:** NGINX
- **Access:** SSH key-based authentication only
- <img width="1068" height="685" alt="Installngnix" src="https://github.com/user-attachments/assets/85ba382a-11d6-475c-83e8-577d662f0b9a" />
<img width="1086" height="705" alt="loginto the Vm" src="https://github.com/user-attachments/assets/2a4f6c01-c763-4db3-a810-0b35cd1cfcc8" />


### Monitoring & Alerting
- **Log Analytics Workspace:** `law-secure-web`
- <img width="1418" height="733" alt="LogChecks" src="https://github.com/user-attachments/assets/5dd83a17-4262-4bf8-8472-20faedb4b77f" />

- **Azure Monitor:** VM performance metrics
- **Alert Rule:** CPU utilization alert (threshold tuned to VM size)
<img width="1399" height="496" alt="securityalert" src="https://github.com/user-attachments/assets/02091356-cd2f-4bc7-8298-a49777bd2d4d" />

---

## Security Controls Implemented

### Network Security
- Subnet-level Network Security Group enforcing least-privilege inbound rules
- No unnecessary open ports
- SSH access restricted to a single trusted IP address

### Access Control
- Password-based SSH disabled
- Key-based authentication enforced
- Administrative access limited to authorized user

### Monitoring & Detection
- Centralized log collection using Azure Monitor and Log Analytics
- Heartbeat telemetry verified for VM connectivity
- CPU alert configured to detect abnormal workload behavior

---
### Web Application Verification
The NGINX web application was accessed successfully via the VM’s public IP address, confirming that inbound HTTP (port 80) traffic is permitted by the Network Security Group.
<img width="1053" height="551" alt="testthewebserv" src="https://github.com/user-attachments/assets/1f5daf65-d387-4db3-86be-eef11faa71a0" />


## Validation & Testing

The following validations were performed:
- Successful SSH access using private key authentication
- Public HTTP access confirmed via browser
- NGINX service verified and serving custom content
- Log ingestion confirmed using Log Analytics `Heartbeat` queries
- CPU alert validated using synthetic load testing

---

## Cost Management
To minimize cloud spend:
- The virtual machine was **stopped (deallocated)** when not in use
- All resources were grouped to allow clean teardown by deleting the resource group

---

## What This Project Demonstrates
- Hands-on experience with Azure networking and NSGs
- Secure VM deployment and access control
- Practical monitoring and alerting configuration
- Understanding of Azure resource organization and lifecycle management
- Cost-aware cloud operations

---

## Possible Enhancements
Future improvements could include:
- Microsoft Defender for Cloud integration
- Azure Bastion for secure browser-based access
- Web Application Firewall (WAF)
- Role-Based Access Control (RBAC) customization
- Infrastructure as Code (ARM/Bicep/Terraform)

---

## Author
**Afi**  
Cloud & Cybersecurity Learner  
