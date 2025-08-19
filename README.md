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
Step 1: Go to RDS Service

Log in to AWS Console

Search for RDS → Open it

Click Create database

Step 2: Choose Engine

Select a database engine (e.g., MySQL or PostgreSQL)

Choose version

Step 3: Select Template

Free tier (good for practice)

Production (with Multi-AZ, backups, etc.)

Step 4: Configure Settings

DB Identifier → mydb

Master username → admin

Master password → enter a secure password

Step 5: Instance Configuration

Instance class → db.t3.micro (free tier)

Storage → General Purpose SSD (20 GB default)

Step 6: Connectivity

VPC → Select your VPC

Public access → Choose Yes if you want to connect from your laptop

VPC Security Group → Allow inbound MySQL/PostgreSQL port (3306 for MySQL, 5432 for PostgreSQL)

Step 7: Additional Settings

Initial Database Name → mydb01

Enable automatic backups (optional for testing)

Step 8: Create Database

Click Create Database

Wait for status → Available
CREATE DATABASE student_db
# Student Registration System (AWS Project)

## Architecture
- **Frontend** → HTML + JS (EC2 Public Subnet with Nginx)
- **Backend** → Node.js Express API (EC2 Private Subnet)
- **Database** → Amazon RDS (MySQL)

## Features
- Student Registration (Name, Email, Course)
- View Registered Students
- Secure 3-Tier AWS Setup

## Steps
1. Setup RDS Database
2. Deploy Backend (Node.js + Express)
3. Deploy Frontend (HTML + Nginx)
4. Configure Security Groups
5. Test Application
