# AWS IAM & Least-Privilege Security Lab

## Overview

This lab demonstrates cross-account AWS access using **IAM users, IAM roles, AWS STS, and least-privilege permissions**.

A user in one AWS account was granted permission to assume an IAM role located in a separate AWS account. The target role provides access to Amazon ECS while intentionally limiting access to other AWS services.

The lab demonstrates how IAM identity policies, role trust policies, AWS STS, and service-specific permissions work together to implement controlled cross-account access.

---

## Objectives

- Configure cross-account IAM access
- Create an IAM role in a separate AWS account
- Configure a role trust policy
- Grant an IAM user permission to assume the role
- Use AWS STS for cross-account role assumption
- Validate successful role assumption
- Demonstrate least-privilege access
- Verify that unauthorized AWS service operations are denied

---

## Architecture
What Was Implemented
IAM User in Account A
Cross-account IAM Role in Account B
Role trust policy
sts:AssumeRole permission
ECS-focused role permissions
Temporary credentials through AWS STS
Least-privilege access model
Validation
Test 1 — Cross-Account Role Assumption

The IAM user successfully assumed the EcsFullAccess role in the second AWS account.

Result: PASS ✅

Test 2 — EC2 Access Restriction

After assuming the role, an attempt was made to launch an EC2 instance.

The operation failed with an AccessDenied error because the role did not have the required EC2 permission.

Result: PASS ✅

Security Concepts
Least Privilege

The role provides access to its intended service scope without automatically granting access to unrelated AWS services.

Cross-Account Access

IAM roles allow controlled access between AWS accounts without creating permanent users in the target account.

Trust Policy vs Permission Policy
Trust policy: Defines who can assume the role.
Permission policy: Defines what the role can do after it is assumed.
AWS STS

AWS Security Token Service provides temporary credentials when the role is assumed.

Technologies
AWS IAM
AWS STS
IAM Users
IAM Roles
IAM Policies
Trust Policies
Amazon ECS
Amazon EC2
AWS Management Console
Key Result

The lab successfully demonstrated cross-account role assumption and least-privilege access, with unauthorized EC2 activity rejected by AWS.

Disclaimer

This is a personal AWS security laboratory environment.

No AWS credentials, access keys, passwords, or secrets are included in this repository.

AWS Account IDs have been redacted from public configuration examples and screenshots.







Account A — Identity Account
│
├── IAM User
│      │
│      │ sts:AssumeRole
│      ▼
│
└──────────────────────────────┐
                               │
                               ▼
                    Account B — Resource Account
                    │
                    └── IAM Role: EcsFullAccess
                              │
                              ▼
                         Amazon ECS
