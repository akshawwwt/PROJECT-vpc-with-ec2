# Terraform AWS High Availability Web Infrastructure

## Project Overview

This Terraform project provisions a fully automated, secure, scalable, and highly available web application infrastructure on AWS. It uses Terraform Infrastructure as Code (IaC) to set up networking, compute resources, security, and load balancing.

## Infrastructure Components

### 1. AWS VPC (Virtual Private Cloud)

* **CIDR Block:** `10.0.0.0/16`
* **Purpose:** Provides isolated networking for enhanced security and controlled network management.

### 2. Public Subnets

* **Subnet 1:** `10.0.0.0/24` in `us-east-1a`
* **Subnet 2:** `10.0.1.0/24` in `us-east-1b`
* **Purpose:** Ensures redundancy, high availability, and load distribution across different AWS availability zones.

### 3. Internet Gateway (IGW)

* **Purpose:** Provides internet connectivity for the public subnets and instances.

### 4. Route Table & Associations

* **Configuration:** Routes all internet-bound traffic (`0.0.0.0/0`) through the IGW.
* **Purpose:** Allows resources within subnets to communicate with the internet.

### 5. Security Group (`webSg`)

* **Inbound Rules:**

  * HTTP (port 80): Public web access
  * SSH (port 22): Secure remote access for management
* **Outbound Rules:** Allow all traffic
* **Purpose:** Controls and restricts access to EC2 instances, maintaining security.

### 6. EC2 Instances

* **AMI:** Ubuntu Linux (`ami-0261755bbcb8c4a84`)
* **Instance Type:** `t2.micro` (Free-tier eligible)
* **User Data:** Automated server setup and Apache web server configuration (files: `userdata.sh`, `userdata1.sh`).

### 7. Application Load Balancer (ALB)

* **Purpose:** Evenly distributes incoming HTTP traffic to EC2 instances, improving reliability and availability.
* **Health Checks:** Ensures only healthy instances receive traffic.

### 8. AWS S3 Bucket

* **Bucket Name:** `akshatterraform2023project`
* **Purpose:** Durable and scalable storage solution for static files, logs, backups, or application assets.

## Usage Instructions

### Step 1: Initialize Terraform

```bash
terraform init
```

### Step 2: Review Terraform Plan

```bash
terraform plan
```

### Step 3: Apply the Terraform Configuration

```bash
terraform apply
```

### Step 4: Access Your Web Application

After successful deployment, access your web application through the Load Balancer DNS URL provided in the Terraform output (`loadbalancerdns`).

## Project Cleanup

To destroy the infrastructure and avoid additional AWS costs:

```bash
terraform destroy
```

## Enhancements and Future Steps

* Implement Auto Scaling Groups for improved scalability and resource optimization.
* Integrate Amazon RDS for managed database storage.
* Set up monitoring and alerting systems (e.g., AWS CloudWatch).
* Establish CI/CD pipelines for streamlined and automated deployments.

## Technologies Used

* Terraform (Infrastructure as Code)
* Amazon Web Services (VPC, EC2, ALB, S3)
* Ubuntu Linux & Apache Web Server

---

This project highlights key DevOps and cloud computing skills, demonstrating practical experience in infrastructure automation, security, scalability, and high availability on AWS.
