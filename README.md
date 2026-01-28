#  Three-Tier CI/CD Pipeline with Jenkins & Terraform (AWS)

This project demonstrates a production-style CI/CD pipeline using Jenkins and Terraform to provision a 3-tier AWS infrastructure with a manual approval gate before deployment.

The pipeline automates infrastructure provisioning while still keeping human control over critical changes.

-----

##  Architecture Overview

The Terraform code provisions the following AWS resources:

- VPC with public and private subnets

- Internet Gateway & Route Tables

- EC2 Web Server

- EC2 Application Server

- RDS MySQL Database

- Security Groups for Web, App, and DB tiers

This represents a classic 3-tier architecture:

``` User → Web Tier → App Tier → Database Tier ```

------ 

## 🛠️ Tech Stack

- CI/CD: Jenkins (Declarative Pipeline)

- IaC: Terraform

- Cloud: AWS

- Version Control: GitHub

- Approval Control: Jenkins Manual Input Stage


📁 Repository Structure
```
three-tier-ci-cd/
├── Jenkinsfile
└── terraform/
    ├── provider.tf
    ├── network.tf
    ├── security.tf
    ├── ec2.tf
    ├── db.tf
    └── tfplan.txt (generated during pipeline run)

``` 

---

##  Jenkins Pipeline Flow

- Checkout CI/CD Repository

- Checkout Terraform Infrastructure Repository

- Terraform Init

- Terraform Plan

- Generate Human-Readable Plan

- Manual Approval Gate

- Terraform Apply or Destroy

- Post-Build Status Reporting

-----


##  Manual Approval Stage (Key Feature)

Before applying any infrastructure changes, Jenkins pauses and displays:

- The full Terraform execution plan

- A manual confirmation prompt

This ensures:

- No accidental infrastructure changes

- Better cost and risk control

- Real-world production behavior

----

##  How to Run This Project
Prerequisites

- Jenkins installed on EC2 or local server

- Terraform installed on Jenkins node

- AWS IAM credentials configured in Jenkins:

    - AWS_ACCESS_KEY_ID

    - AWS_SECRET_ACCESS_KEY

-----

## Steps

- Create a Jenkins Pipeline job

- Point SCM to this repository

- Run the pipeline

- Review the Terraform plan

- Approve the manual step

- Infrastructure is provisioned on AWS 🚀

-----------


##  Security Notes

- AWS credentials are securely stored in Jenkins Credentials Manager

- Sensitive Terraform values are not hard-coded

- Database credentials are marked as sensitive

----


## 📌 Key Learnings

- Correct Terraform execution directory is critical

- Jenkins workspace paths must align with Terraform output files

- Manual approvals prevent unintended production changes

- Infrastructure pipelines should be repeatable and auditable

-------


## Future Enhancements

- Remote Terraform backend (S3 + DynamoDB)

- Application deployment stages

- Load balancer integration

- Jenkins shared libraries

- Cost estimation before approval

-----


## 👤 Author

Gowri
Cloud | DevOps | AWS | Terraform | Jenkins
