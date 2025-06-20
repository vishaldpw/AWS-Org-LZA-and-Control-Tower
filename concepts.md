# 🏢 AWS-Org-LZA-and-Control-Tower

I am trying to explain **AWS Organizations**, **AWS Control Tower**, and **AWS Landing Zone Accelerator (LZA)** concepts in simple words.

---

## 🏢 AWS Organizations

> _"I want to manage multiple AWS accounts."_  

- It gives the foundation to **link and organize accounts centrally**.
- Allows centralized billing, policy control, and account structure using **Organizational Units (OUs)**.

---

## 🛫 AWS Control Tower

> _"I want AWS to help me create and manage a well-architected multi-account setup with guardrails, logging, and centralized governance."_  

- A higher-level service that uses **AWS Organizations**, **AWS Config**, and more.
- Helps **set up and govern** a secure, multi-account AWS environment.
- Provides automation + governance out-of-the-box.

---

## 🚀 AWS Landing Zone Accelerator (LZA)

> _"I need a more secure, compliant, and highly customized environment — LZA extends what Control Tower does."_  

- Built **on top of AWS Control Tower**.
- Offers advanced security, compliance, DNS, and baseline configurations.
- Ideal for **regulated enterprises** with complex needs.

---

## 🧰 What tools and features does AWS Control Tower offer?

### 🧱 1. AWS Organizations
- Used in the background to create and manage accounts.

### 🧾 2. Account Factory
- A **self-service account vending machine**.
- Helps you create new AWS accounts in a **standardized** way.
- Supports both GUI and **Terraform via AFT (Account Factory for Terraform)**.

### 🛡️ 3. Guardrails (Preventive & Detective)
- Built using **AWS Config** and **Service Control Policies (SCPs)**.
- Helps enforce rules like:
  - No public S3 buckets
  - Require CloudTrail enabled
  - No changes to IAM policies

### 📜 4. AWS Config Rules
- Used for **compliance checks**.
- Ensures accounts **stay compliant** with organizational policies.

### 📦 5. Centralized Logging
- Uses **AWS CloudTrail** and **S3**.
- All logs from all accounts are sent to a **centralized logging account**.

### 🔐 6. AWS IAM Identity Center (formerly AWS SSO)
- Optional component.
- Manages **user access across accounts** centrally.

### ⚙️ 7. Lifecycle Events & Notifications
- Triggered when:
  - New accounts are created
  - Guardrails are violated
  - Resource drifts occur
- Uses **Amazon SNS** for alerts.

### 🔧 8. Integration with AWS CloudFormation / Terraform
- Extend Control Tower with:
  - **Customizations for Control Tower (CfCT)**
  - **Account Factory for Terraform (AFT)**

---

## 📋 Summary

| **Tool/Service**       | **Purpose**                                                       |
|------------------------|-------------------------------------------------------------------|
| AWS Organizations      | Foundation for managing multi-account setups                     |
| AWS Control Tower      | Automates secure account setup, applies guardrails, logging      |
| LZA                    | Enterprise-level extension with advanced security & compliance    |
| Account Factory        | Self-service portal to create accounts                           |
| Guardrails             | Preventive (SCPs) and Detective (Config Rules) controls           |
| CloudTrail + S3        | Centralized logging                                               |
| IAM Identity Center    | Central access management (optional)                             |
| AFT / CfCT             | Infrastructure-as-code to extend Control Tower                   |

---

![Architecture Diagram](https://github.com/user-attachments/assets/013854d9-b9dd-4d42-b5b1-909d83783739)
