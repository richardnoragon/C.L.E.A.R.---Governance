# Linter Enforcement

Linters provide fast, local, developer‑friendly enforcement of standards before code
reaches CI. They are the first line of defense against violations and drift.

Linter rules ensure that contributors receive immediate feedback, reducing friction
and improving adoption.

---

## Purpose

- Enforce syntactic and stylistic standards  
- Validate naming conventions, file structures, and metadata  
- Catch violations early in the development workflow  
- Provide consistent rules across repositories  

---

## What Belongs in This Directory

- Linter configuration files (ESLint, Stylelint, Pylint, etc.)  
- Custom rule definitions  
- Shared rule sets  
- Documentation for integrating linters into local workflows  

---

## Principles

- Linter rules MUST reflect the approved specification  
- Linter rules MUST be deterministic  
- Linter rules SHOULD be fast and developer‑friendly  
- Linter rules SHOULD be consistent across repositories  

---

## Steward Verification

The Steward ensures that:

- Linter rules match the approved standard  
- No rule introduces new governance requirements  
- Documentation is complete and clear  
