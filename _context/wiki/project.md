# Project Overview

## What this project is

`ibm-namespace-scope-operator` extends RBAC permissions of CPfs and Cloud Pak operators to namespaces outside their own. It is only installed when CPfs runs in **OwnNamespace mode** and operators need to manage operands across multiple namespaces.

It works by copying Roles from opted-in operators and binding them to those operators' ServiceAccounts in the target namespaces, effectively granting cross-namespace permissions without requiring AllNamespace mode.

## Main goals

1. **Cross-namespace RBAC extension** — allow OwnNamespace-mode operators to act in additional namespaces.
2. **Support OwnNamespace CPfs deployments** — prerequisite only when this combination of conditions applies.
3. **Bug fixes** — primary ongoing work.

## Key stakeholders / users

- **CPfs platform team** — maintainers.
- **IBM Cloud Pak teams** — consume this when deploying CPfs or their own operators in OwnNamespace mode with multi-namespace operand management.
- **End customers** — indirectly, through Cloud Pak installations.

## Installation conditions

This operator is only needed when **all** of the following are true:
1. CPfs (or a Cloud Pak) is installed in **OwnNamespace mode**
2. The operator needs to manage operands in **multiple namespaces**

If CPfs is installed in AllNamespace mode, this operator is not used.

## Key CRDs

| CRD | Purpose |
|-----|---------|
| `NamespaceScope` | Defines which operators are opted in and which namespaces they should receive extended RBAC for |

## Operating modes

| Mode | Behaviour |
|------|-----------|
| **Automatic** (default) | Operator extends RBAC to target namespaces automatically for opted-in operators |
| **Manual** | A user must explicitly authorize the operator before it will copy RBAC to target namespaces |

The automatic vs. manual distinction is a common source of support issues — always clarify which mode is active when debugging RBAC-related problems.

## Key workflows

- **Bug fixes** — most common work.
