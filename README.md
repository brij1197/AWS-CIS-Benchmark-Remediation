
# AWS Security Hub Automated Remediation

This repository provides a framework for automating remediation of security and compliance issues detected by AWS Security Hub. By leveraging EventBridge, Lambda functions, and CloudFormation, it enables targeted, automated fixes for compliance violations, aligning with AWS CIS benchmarks.

## Overview

AWS Security Hub aggregates visibility into security and compliance statuses across multiple AWS accounts. This solution automates the remediation of non-compliant findings based on custom actions, enabling seamless enforcement of security best practices.

### Key Features:
- Automated remediation of IAM password policy violations and security group compliance issues.
- Event-driven architecture using EventBridge and Lambda functions.
- Scalable deployment across multiple AWS accounts using CloudFormation StackSets.
- Example use cases for common AWS compliance challenges.

---

## How It Works

1. **Security Findings:**  
   AWS Security Hub identifies compliance issues, such as insecure IAM password policies or misconfigured security groups.

2. **EventBridge Rules:**  
   Findings are sent to EventBridge, which triggers Lambda functions based on custom actions mapped to specific finding types.

3. **Lambda Functions:**  
   Targeted Lambda functions process the findings and apply necessary remediations automatically.

4. **Compliance Verification:**  
   Security Hub reflects compliance updates within 12 hours of remediation.

---

## Examples of Automated Remediation

### 1. Security Group Compliance  
**Scenario:**  
A security group allows unrestricted SSH access from all sources, violating AWS CIS policies.

**Remediation:**  
- A Lambda function removes the non-compliant ingress rule from the security group.
- Compliance is restored, and Security Hub reflects the update within 12 hours.

**Automation:**  
- EventBridge rule triggers the Lambda function whenever a security group violation is detected.

### 2. IAM Password Policy Compliance  
**Scenario:**  
User accounts have passwords that are not rotated every 90 days.

**Remediation:**  
- A Lambda function enforces password policies, ensuring users comply with password age requirements.

**Automation:**  
- EventBridge rule triggers the Lambda function when a password policy violation is identified.

---

## Deployment Instructions

1. **EventBridge Setup:**  
   - Configure EventBridge rules for findings from AWS Security Hub.

2. **Lambda Functions:**  
   - Deploy Lambda functions for specific remediation tasks (e.g., password policies, security groups).

3. **CloudFormation StackSets:**  
   - Use CloudFormation StackSets to deploy roles with necessary permissions across multiple AWS accounts.

---

## Table of Contents
1. [IAM Password Policy Remediation](#1-iam-password-policy-remediation)
2. [Security Group Compliance Remediation](#2-security-group-compliance-remediation)

---

### 1. IAM Password Policy Remediation
**File:** `cis_password_policy_lambda`  
**Description:**  
- Lambda function to enforce IAM password policies.
- Ensures compliance with rules like password expiration (e.g., every 90 days).

---

### 2. Security Group Compliance Remediation
**File:** `cis_security_group_lambda`  
**Description:**  
- Lambda function to remediate security group violations.
- Automatically updates inbound/outbound rules to align with AWS CIS policies.

---

## Future Enhancements
- Add remediation for additional AWS CIS controls.
- Provide a dashboard for tracking remediation status.
- Integrate with third-party tools for expanded visibility.

---
