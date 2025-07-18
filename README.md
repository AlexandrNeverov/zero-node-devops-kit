# Zero Node DevOps Kit 🚀

[![Terraform AWS Kit Demo](https://raw.githubusercontent.com/AlexandrNeverov/zero-node-devops-kit/main/image.png)](https://www.youtube.com/watch?v=_W2HxS0K1PE)

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

5. ☁️ 📦 Install via cURL (infra-bootstrap):
```bash
curl -v https://raw.githubusercontent.com/AlexandrNeverov/zero-node-devops-kit/refs/heads/main/infra-bootstrap/aws-zero-node-bootstrap.sh | bash -
```

6. ☁️ 📦 Install via cURL (bootstrap-zero-node-tools):
```bash
curl -v https://raw.githubusercontent.com/AlexandrNeverov/zero-node-devops-kit/refs/heads/main/bootstrap-zero-node-tools.sh | bash -
```

7. ☁️ 📦 Install via cURL (setup-terraform-s3-dynamodb):
```bash
curl -v https://raw.githubusercontent.com/AlexandrNeverov/zero-node-devops-kit/refs/heads/main/setup-terraform-s3-dynamodb.sh | bash -
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
DevOps Engineer · Cloud & Infrastructure Automation · Industry PhD

- **GitHub:** [AlexandrNeverov](https://github.com/AlexandrNeverov)  
- **LinkedIn:** [linkedin.com/in/alexneverov](https://www.linkedin.com/in/alexneverov)  
- **Upwork:** [upwork.com/freelancers/~01c616035669bbf379](https://www.upwork.com/freelancers/~01c616035669bbf379)  
- **Website:** [neverov-it.com](https://neverov-it.com) · [neverov-science.com](https://neverov-science.com)  
- **Email:** [alex@neverov-it.com](mailto:alex@neverov-it.com)  
- **Phone:** +1 (754) 236‑5715
