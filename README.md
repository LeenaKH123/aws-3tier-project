# AWS 3-Tier Architecture — Terraform

A Terraform implementation of the classic **3-tier cloud architecture pattern** on AWS: a presentation layer, application layer, and data layer — each isolated in its own subnet with appropriate security controls.

This is the foundational architecture used in enterprise cloud deployments across banking, telco, and government sectors.

---

## Architecture Overview

```
Internet
    │
    ▼
[ Application Load Balancer ]   ← Public Subnet (Presentation Tier)
    │
    ▼
[ EC2 / Application Layer ]     ← Private Subnet (Application Tier)
    │
    ▼
[ RDS / Database Layer ]        ← Private Subnet (Data Tier)
```

---

## Infrastructure Components

```
├── main.tf              # VPC, subnets, EC2, RDS, ALB, security groups
├── variables.tf         # Configurable input parameters
├── outputs.tf           # Key resource outputs (ALB DNS, DB endpoint, etc.)
├── provider.tf          # AWS provider and region configuration
└── .terraform.lock.hcl  # Provider dependency lock
```

---

## AWS Services Used

`VPC` · `Public & Private Subnets` · `EC2` · `Application Load Balancer` · `RDS` · `Security Groups` · `IAM` · `Internet Gateway` · `NAT Gateway`

---

## Key Concepts Demonstrated

- **Network segmentation** — strict separation of public and private tiers via subnets and security groups
- **Least privilege networking** — application tier cannot be reached directly from the internet; database tier only accepts traffic from the application tier
- **High availability** — multi-AZ design with load balancing across the presentation layer
- **Infrastructure as Code** — entire stack defined in Terraform, deployable in minutes
- **Enterprise architecture pattern** — mirrors patterns used in regulated industries (banking, telco, government)

---

## Prerequisites

- Terraform >= 1.0
- AWS CLI configured with appropriate IAM permissions

---

## Usage

```bash
terraform init
terraform plan
terraform apply
```

---

## Author

**Leena Al-Khalili** — Digital Transformation Leader | AWS Solutions Architect  
[LinkedIn](https://www.linkedin.com/in/leena-alkhalili/) · [GitHub](https://github.com/LeenaKH123)

