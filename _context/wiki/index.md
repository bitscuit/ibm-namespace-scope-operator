# ibm-namespace-scope-operator Wiki

Operator that extends RBAC permissions of CPfs (and Cloud Pak) operators to additional namespaces. Only required when CPfs is installed in OwnNamespace mode with multi-namespace operand management.

## Contents

| File | What's in it |
|------|-------------|
| [project.md](project.md) | Project overview, goals, automatic vs manual mode, installation conditions |
| [preferences.md](preferences.md) | Working standards, coding style, AI collaboration preferences |

## Quick orientation

- Only installed when CPfs runs in **OwnNamespace mode** and needs to manage operands across multiple namespaces.
- Extends RBAC by copying Roles from opted-in operators and binding them to their ServiceAccounts in target namespaces.
- **Two modes:** automatic (default — extends RBAC automatically) and manual (user must explicitly authorize).
- Manages the `NamespaceScope` CRD.
- Most work is **bug fixes**.
