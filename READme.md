# Terraform AWS Web Application Infrastructure

## Project Overview

This project automates the deployment of a secure, scalable, and highly available web application infrastructure on AWS using Terraform. It includes VPC networking, EC2 servers, load balancing, and object storage.

## Infrastructure Components

### 1. **AWS VPC (Virtual Private Cloud)**

* **CIDR Block**: `10.0.0.0/16`
* Creates an isolated network for security and clear traffic management.

### 2. **Public Subnets**

* **Subnet 1:** `10.0.0.0/24` (Availability Zone: `us-east-1a`)
* **Subnet 2:** `10.0.1.0/24` (Availability Zone: `us-east-1b`)
* Provides redundancy and high availability across two AWS availability zones.

### 3. **Internet Gateway (IGW)**

* Enables internet connectivity for instances within the public subnets.

### 4. **Route Table and Associations**

* Defines routing to direct all internet-bound traffic (`0.0.0.0/0`) through the Internet Gateway.
* Ensures subnets have internet access.

### 5. **Security Group**

* **Ingress Rules:**

  * HTTP (port 80): Allows public web access
  * SSH (port 22): Enables secure server management
* Protects instances by allowing only essential traffic.

### 6. **EC2 Instances**

* **AMI:** Ubuntu Linux (`ami-0261755bbcb8c4a84`)
* **Type:** `t2.micro` (Free tier eligible)
* **User Data Scripts:** Automate initial server setup and app deployment

  * `userdata.sh` for instance 1
  * `userdata1.sh` for instance 2

### 7. **Application Load Balancer (ALB)**

* Distributes incoming HTTP traffic between two EC2 instances.
* Performs regular health checks to ensure instance availability.

### 8. **AWS S3 Bucket**

* **Bucket Name:** `akshatterraform2023project`
* Provides scalable, durable storage for application assets, logs, or backups.

## Deployment Steps

### 1. **Initialize Terraform:**

```bash
terraform init
```

### 2. **Review Terraform Plan:**

```bash
terraform plan
```

### 3. **Apply Terraform Configuration:**

```bash
terraform apply
```

### 4. **Access Your Web Application:**

* After successful deployment, access your application via the Application Load Balancer URL output (`loadbalancerdns`).

## Cleanup

To avoid unwanted charges, destroy all created resources:

```bash
terraform destroy
```

## Improvements & Next Steps

* Implement auto-scaling groups for enhanced scalability.
* Integrate managed databases like Amazon RDS for data persistence.
* Set up CI/CD pipelines for automated deployments.
* Configure monitoring and alerting with AWS CloudWatch.

## Technologies Used

* Terraform (Infrastructure as Code)
* AWS (VPC, EC2, ALB, S3)

---

This project demonstrates core DevOps and cloud engineering skills, including infrastructure automation, high availability design, security best practices, and efficient resource management.
