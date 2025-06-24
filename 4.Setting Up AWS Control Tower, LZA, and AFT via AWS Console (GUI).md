# 🛠️ Setting Up AWS Control Tower, LZA, and AFT via AWS Console (GUI)

This guide walks you through the high-level steps to set up **Landing Zone Accelerator (LZA)** and **Account Factory for Terraform (AFT)** using the **AWS Management Console (GUI)**, focusing especially on **AWS Service Catalog** usage.

---

## 🏗️ Prerequisites

- An AWS Organization-enabled account with **Admin privileges**
- AWS Control Tower available in your preferred region
- IAM Identity Center (SSO) will be enabled as part of the process
- (Optional) An AWS CodeCommit or GitHub repo to store AFT configurations

---

## 🔹 Step 1: Enable AWS Control Tower & IAM Identity Center

1. Open the **AWS Console**
2. Go to **Control Tower**
3. Click **Set up landing zone**
4. Proceed through the guided wizard to:
   - Enable Control Tower
   - Create the `Audit` and `Log archive` accounts
   - Set up **IAM Identity Center**
   - Choose an initial organizational unit (OU) such as `Core`

📌 Note: IAM Identity Center will be auto-configured if not already set.

---

## 🔹 Step 2: Create Additional Organizational Units (Optional but Recommended)

1. Open **AWS Organizations** from the console
2. Create at least one additional OU, e.g. `Workloads`, `Sandbox`, or `Dev`
3. Go back to **Control Tower → Organizational Units**
4. Enroll the new OU(s)

---

## 🔹 Step 3: Enable AWS Config Across All Accounts

1. Go to **AWS Config** in the console
2. Enable AWS Config in:
   - Management (root) account
   - Log archive and Audit accounts
   - Any existing enrolled accounts
3. (Optional) Set up an **Aggregator** for centralized compliance visibility

---

## 🔹 Step 4: Deploy Landing Zone Accelerator (LZA)

1. Open **AWS Service Catalog**
2. Search for **Landing Zone Accelerator on AWS**
3. Launch the product by clicking **Launch Stack**
4. Provide configuration parameters:
   - Logging, SNS topics, Config bucket
   - SCP settings, OU targets, security account IDs

🛡️ LZA enhances your Control Tower setup with security best practices, network baselining, SCPs, and additional controls.

---

## 🔹 Step 5: Deploy AFT from AWS Service Catalog

### 📘 What is AWS Service Catalog?

AWS **Service Catalog** allows administrators to create and manage approved products (CloudFormation stacks, Terraform configurations, etc.) for others to launch easily and consistently.

- AFT (Account Factory for Terraform) is published as a **Service Catalog product** by AWS.
- This makes deploying AFT a **click-based experience** from the console.

### ✅ How to Deploy AFT

1. Go to **AWS Service Catalog** from the console
2. Under **Portfolios**, search for:
