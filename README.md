# Zero Node DevOps Kit 🚀

A fully automated starter kit to bootstrap a secure EC2 node, install DevOps tools, and configure Terraform backend on AWS (S3 + DynamoDB).

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

**Alexandr Neverov**  
GitHub: [AlexandrNeverov](https://github.com/AlexandrNeverov)
