# 🚀 AWS EKS Cluster Deployment using Terraform

This project provisions a production-ready Amazon Elastic Kubernetes Service (EKS) cluster on AWS using Terraform. It follows Infrastructure as Code (IaC) best practices with a modular and reusable structure, making it easy to deploy, manage, and scale Kubernetes clusters across multiple environments.

---

## 📌 Project Overview

This Terraform project automates the deployment of an AWS EKS cluster along with the required networking and compute infrastructure.

The infrastructure includes:

- Amazon EKS Cluster
- Managed Node Group
- VPC with Public & Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups
- IAM Roles & Policies
- Outputs for Kubernetes configuration

---

## 🏗️ Architecture

```
AWS Account
│
├── VPC
│   ├── Public Subnets
│   │     ├── NAT Gateway
│   │     └── Internet Gateway
│   │
│   └── Private Subnets
│         └── EKS Worker Nodes
│
├── EKS Control Plane
│
├── Managed Node Group
│
└── IAM Roles & Security Groups
```

---

## 📂 Project Structure

```
eks-terraform/
│
├── modules/
│   ├── vpc/
│   ├── eks/
│   ├── iam/
│   └── security-group/
│
├── environments/
│   ├── dev/
│   ├── stage/
│   └── prod/
│
├── backend.tf
├── provider.tf
├── variables.tf
├── outputs.tf
├── terraform.tfvars
├── versions.tf
└── README.md
```

---

## 🛠️ Prerequisites

Before deploying, ensure you have:

- AWS Account
- AWS CLI configured
- Terraform >= 1.5
- kubectl
- Git
- IAM User with Administrator permissions (or appropriate permissions)

Verify installation:

```bash
terraform -version
aws --version
kubectl version --client
```

---

## ⚙️ Configure AWS Credentials

```bash
aws configure
```

Provide:

- AWS Access Key
- AWS Secret Access Key
- Region
- Output Format

---

## 🚀 Deployment

### 1. Clone Repository

```bash
git clone https://github.com/yourusername/eks-terraform.git

cd eks-terraform
```

---

### 2. Initialize Terraform

```bash
terraform init
```

---

### 3. Validate Configuration

```bash
terraform validate
```

---

### 4. Review Execution Plan

```bash
terraform plan
```

---

### 5. Deploy Infrastructure

```bash
terraform apply
```

Type:

```
yes
```

Terraform will provision:

- VPC
- Networking
- IAM Roles
- Security Groups
- EKS Cluster
- Managed Node Group

---

## 🔗 Connect to the Cluster

Update kubeconfig:

```bash
aws eks update-kubeconfig \
--region <region> \
--name <cluster-name>
```

Verify connection:

```bash
kubectl get nodes
```

Expected output:

```
NAME                     STATUS   ROLES    AGE
ip-10-0-1-15.ec2.internal Ready    <none>   2m
```

---

## 📊 Useful Terraform Commands

Initialize:

```bash
terraform init
```

Format:

```bash
terraform fmt
```

Validate:

```bash
terraform validate
```

Plan:

```bash
terraform plan
```

Apply:

```bash
terraform apply
```

Destroy:

```bash
terraform destroy
```

---

## 🔒 Security Best Practices

- Store Terraform state remotely (Amazon S3 + DynamoDB Locking)
- Never commit `.tfstate` files
- Use IAM roles instead of long-term credentials
- Keep worker nodes in private subnets
- Restrict Security Group rules
- Enable encryption for EKS secrets
- Use versioned Terraform modules

---

## 🌍 Supported Environments

- Development
- Staging
- Production

Each environment maintains its own Terraform state and variables.

---

## 📦 Technologies Used

- Terraform
- AWS EKS
- Amazon VPC
- IAM
- EC2 Managed Node Groups
- AWS CLI
- kubectl
- Git

---

## 📈 Future Enhancements

- Helm deployment automation
- ArgoCD
- AWS Load Balancer Controller
- Cluster Autoscaler
- Metrics Server
- Prometheus & Grafana
- External DNS
- Karpenter
- GitHub Actions CI/CD

---

## 🧹 Cleanup

Destroy all infrastructure:

```bash
terraform destroy
```

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch

```bash
git checkout -b feature/new-feature
```

3. Commit your changes

```bash
git commit -m "Add new feature"
```

4. Push the branch

```bash
git push origin feature/new-feature
```

5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

**Shiveen Sharma**

Cloud & DevOps Enthusiast

- AWS Solutions Architect Associate (SAA-C03)
- Terraform
- Docker
- Linux
- Git & GitHub
- Kubernetes