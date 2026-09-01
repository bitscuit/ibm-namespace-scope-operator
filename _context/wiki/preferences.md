# Working Preferences & Standards

## How I use AI

- **Bug fixes** — the most common use case. Understand the problem before suggesting a fix.
- **Understanding RBAC behaviour** — tracing why permissions are or aren't being propagated in automatic vs. manual mode.
- **Understanding unfamiliar code** — orientation to areas not recently touched.

## Communication preferences

- Be direct and technical. No filler phrases ("Great!", "Certainly!", etc.).
- Investigate before answering — never speculate about code you haven't read.
- When explaining unfamiliar code: start with what it *does*, then how it works.
- Flag assumptions explicitly.

## Code style & engineering standards

- **Minimal changes.** Produce the smallest diff that solves the problem. No opportunistic refactors.
- **Trace every changed line** back to the stated requirement.
- **Go conventions.** Follow standard Go idioms and the existing style in the file being edited.

## What to be careful about

- **Automatic vs. manual mode.** Always clarify which mode is active before debugging RBAC propagation issues — behaviour is completely different between the two.
- **Installation conditions.** This operator is only relevant in OwnNamespace + multi-namespace scenarios. Changes should not assume AllNamespace context.
- **RBAC copying is additive but not always reversible.** Be careful with changes that affect how Roles are cleaned up when a namespace is removed from scope.
