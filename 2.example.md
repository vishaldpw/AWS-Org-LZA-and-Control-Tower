# 🔧 Step-by-Step Real-World AWS Setup for AcmeTech Inc.

## ✅ 1. AWS Organizations Setup

**Management Account:** Root account  
**Organizational Units (OUs):**
- Security
- Infrastructure
- Sandbox
- Workloads

---

## ✅ 2. Enable AWS Control Tower

Control Tower sets up the following accounts automatically:

| **Account Name**   | **Purpose**                                              |
|--------------------|----------------------------------------------------------|
| Audit Account      | Stores CloudTrail logs, AWS Config logs                  |
| Log Archive        | Stores all logs from all accounts centrally              |
| Shared Services    | Hosts services like DNS, Active Directory, CI/CD tools   |
| Account Factory    | Used to create new project or team accounts              |

### 🔐 Mandatory Guardrails Enabled:
- CloudTrail must be enabled  
- Config cannot be disabled  
- Logging buckets cannot be deleted  

### 🛡️ Optional Guardrails:
- Disallow changes to IAM policies  
- Disallow internet access in certain OUs  

---

## ✅ 3. Accounts Created via Account Factory

| **OU**      | **Accounts Created**                      |
|-------------|-------------------------------------------|
| Workloads   | `dev-app1`, `qa-app1`, `prod-app1`        |
| Sandbox     | `developer-vishal`, `developer-anita`     |

Each account:
- Inherits security policies (SCPs)  
- Sends logs to central S3 bucket  
- Has limited permissions per OU  

---

## ✅ 4. Guardrails in Action

Examples of Control Tower guardrails applied:

- ❌ Dev accounts **cannot create internet-facing ELBs**  
- ✅ Prod accounts **must have CloudTrail enabled**  
- ❌ No account can use **root user**  

---

## ✅ 5. IAM Identity Center (SSO)

Access setup for users:
- Developers: Access to only `dev-*` accounts  
- Operations Team: Access to all `prod-*` accounts  
- Security Team: Access to everything via `Audit` and `Security` accounts  

---

## 🔒 Optional Step: Add AWS Landing Zone Accelerator (LZA)

AcmeTech adds LZA to meet ISO 27001 & NIST 800-53 requirements.

### 🚀 LZA Features:
- Enforce encryption policies  
- Centralized DNS (Route53 Resolver rules)  
- Advanced logging (VPC flow logs, GuardDuty, Macie)  
- Automate account baselines (e.g., install security agents)  

---

## 🧩 Final Architecture Overview

```text
AWS Organizations
│
├── AWS Control Tower (enabled in root/management account)
│   ├── Sets up Log Archive, Audit, Shared Services accounts
│   ├── Applies Guardrails (SCPs + Config)
│   └── Enables Account Factory (for Dev/Prod/Sandbox accounts)
│
├── IAM Identity Center (SSO for access control)
│
└── [Optional] AWS Landing Zone Accelerator
    ├── Adds compliance framework (NIST, CIS, ISO)
    ├── Advanced DNS, logging, security features
    └── Extends Control Tower setup
```

---

## 🎯 Benefits for AcmeTech

- 🔒 Secure, governed setup from Day 1  
- 🧪 Isolated environments (`dev` / `qa` / `prod`)  
- 🔍 Central visibility of logs and security  
- 🧰 Easy scaling with Account Factory  
- 🚀 Compliance-ready with LZA  

![Architecture Diagram](https://github.com/user-attachments/assets/352d7078-f7b5-4cf7-a969-41fd6f8e45d1)
