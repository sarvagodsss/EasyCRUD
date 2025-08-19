Student Registration System
🖥️ Step 1: Create VPC

Go to VPC service → Create VPC

Select → VPC Only

Name → MyVPC

CIDR Block → 10.0.0.0/16

Tenancy → Default

Click Create VPC

🖥️ Step 2: Create Subnets

Go to Subnets → Create Subnet

Select MyVPC

Create Public Subnet:

Name: PublicSubnet

CIDR Block: 10.0.1.0/24

AZ: us-east-1a

Enable Auto-assign public IP

Create Private Subnet:

Name: PrivateSubnet

CIDR Block: 10.0.2.0/24

AZ: us-east-1b

🖥️ Step 3: Create Internet Gateway

Go to Internet Gateways → Create Internet Gateway

Name → MyIGW

Attach it to MyVPC

🖥️ Step 5: Create Route Tables

Go to Route Tables → Create Route Table

Public Route Table:

Name → PublicRT

VPC → MyVPC

Add Route → 0.0.0.0/0 → Target = Internet Gateway

Associate with Public Subnet


🖥️ Step 6: Launch EC2 Instances

Go to EC2 → Launch Instance

Public EC2 (Web Server):

Name: StudentApp

AMI: Ubuntu

Instance Type: t2.medium

Subnet: PublicSubnet

Auto-assign Public IP: Enabled

Security Group → Allow SSH (22) + HTTP (80) + All Traffic (3306)
