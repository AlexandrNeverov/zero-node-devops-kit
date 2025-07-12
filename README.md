# Zero Node DevOps Kit 🚀


## 🚀 Why This Matters

Provisioning cloud infrastructure from scratch often requires several manual steps: launching an EC2 instance, installing essential tools (like Terraform and AWS CLI), configuring IAM roles, setting up a secure remote backend with S3 and DynamoDB, and managing SSH keys.

**`zero-node-devops-kit` solves this problem with automation.**

This toolkit provides a fully scripted, repeatable way to:

- Launch a ready-to-use EC2 instance ("Zero Node") with an IAM role and public IP
- Install a full suite of DevOps tools (Terraform, AWS CLI, Git, jq, htop, etc.)
- Set up a secure Terraform remote backend using S3 (with versioning) and DynamoDB (for state locking)
- Generate the required backend configuration block for Terraform

Ideal for fast project bootstrapping, infrastructure experimentation, interview readiness, and DevOps skill showcasing.

---

## ✅ Features

- One-click EC2 launch via AWS CLI
- Automated system bootstrap (Git, AWS CLI, Terraform, Python, etc.)
- Terraform backend provisioning (S3 bucket + DynamoDB lock table)
- Clear modular scripts
- Cloud-ready and reproducible

---

## 🛠️ Scripts Overview

| Script                                  | Purpose                                                        |
|-----------------------------------------|----------------------------------------------------------------|
| `infra-bootstrap/aws-zero-node-bootstrap.sh` | Launch EC2 with IAM role, public IP, and security groups       |
| `bootstrap-zero-node-tools.sh`         | Install DevOps tools (Terraform, Git, Python, AWS CLI, etc.)   |
| `setup-terraform-s3-dynamodb.sh`       | Provision S3 bucket + DynamoDB table for Terraform remote state|

---

## 🚀 Quick Start

1. ✅ Launch EC2 via AWS CLI:
```bash
bash infra-bootstrap/aws-zero-node-bootstrap.sh
```

2. 🔐 SSH into the instance:
```bash
ssh -i ~/.ssh/My_mac.pem ubuntu@<PUBLIC_IP>
```

3. ⚙️ Bootstrap DevOps tools:
```bash
bash bootstrap-zero-node-tools.sh
```

4. ☁️ Setup Terraform backend (S3 + DynamoDB):
```bash
bash setup-terraform-s3-dynamodb.sh
```

---

## 📦 Terraform Remote Backend Example

```hcl
terraform {
  backend "s3" {
    bucket         = "terraform-backend-zero-<timestamp>"
    key            = "terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-locks-zero-<timestamp>"
    encrypt        = true
  }
}
```

---

## 🧪 Requirements

- AWS CLI configured (`aws configure`)
- EC2 key pair created (`My_mac`)
- IAM permissions to create EC2, IAM roles, S3, DynamoDB

---

## 📄 License

MIT – free to use, modify, share.

---

## 👨‍💻 Author

**Alex Neverov**  
GitHub: [AlexandrNeverov](https://github.com/AlexandrNeverov)
LinkedIn: https://www.linkedin.com/in/alexneverov/
Web: https://neverov-it.com/ and https://neverov-science.com/
Email: alex@neverov-it.com
UpWork: https://www.upwork.com/freelancers/~01c616035669bbf379
Phone: +1 (754) 236-57-15
