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

```text
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
