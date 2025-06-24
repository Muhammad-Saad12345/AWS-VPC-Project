# 🌐 AWS VPC Project: Secure Public & Private Subnets with NAT Gateway & S3 VPC Endpoint
![Architecture](E:/SMIT/project/VPC04 vpc-endpoint.drawio.png)

This project demonstrates a real-world AWS Virtual Private Cloud (VPC) architecture using Public and Private subnets, NAT Gateway, and VPC Endpoint to securely access AWS S3 without using the public internet.

---

## 🧱 Architecture Overview

- **1 VPC**
- **1 Public Subnet** (with EC2 + Internet Gateway)
- **1 Private Subnet** (with EC2)
- **NAT Gateway** (for internet access from Private EC2)
- **VPC Endpoint (Gateway Type)** for secure access to Amazon S3
- **Route Tables** for public and private routing
- **Security Groups** to allow SSH and internal access

---

## 🗂️ CIDR Blocks

| Component        | CIDR Block        |
|------------------|-------------------|
| VPC              | `10.0.0.0/16`     |
| Public Subnet A  | `10.0.0.0/24`     |
| Private Subnet B | `10.0.1.0/24`     |


## 🔐 Security Group Rules

**Public EC2**:
- Inbound: SSH (Port 22) from `My IP`

**Private EC2**:
- Inbound: SSH from Public Subnet CIDR (e.g. `10.0.0.0/24`)

---

## 🧪 Testing

- SSH into Public EC2 using PEM
- From there, SSH into Private EC2 using private IP
- Test S3 Access:
  ```bash
  aws s3 ls
