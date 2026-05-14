# Specification Anti‑Patterns

Specification anti‑patterns weaken clarity, reduce enforceability, and create long‑term maintenance risks.  
This document identifies common pitfalls in writing standards and how to avoid them.

---

## 1. Vague Language
Using “try to”, “prefer to”, “should consider”, or other soft phrasing.

**Why it’s harmful:**  
Impossible to enforce or review.

**Prevention:**  
Use normative language (MUST, MUST NOT, SHOULD).

---

## 2. Hidden Constraints
Critical context exists only in chat threads or tribal knowledge.

**Why it’s harmful:**  
Reviewers cannot evaluate the proposal accurately.

**Prevention:**  
All constraints must be documented in the specification.

---

## 3. Over‑Scoping
One standard attempts to solve multiple unrelated problems.

**Why it’s harmful:**  
Creates complexity and confusion.

**Prevention:**  
Split into multiple focused standards.

---

## 4. Under‑Scoping
A standard that only applies to one team’s edge case.

**Why it’s harmful:**  
Misuses governance and creates noise.

**Prevention:**  
Governance is for cross‑team rules.

---

## 5. Unenforceable Rules
Standards that cannot be checked mechanically.

**Why it’s harmful:**  
Leads to inconsistent adoption.

**Prevention:**  
Every standard must include an enforcement strategy.

---

## 6. Missing Rationale
Specification states *what* but not *why*.

**Why it’s harmful:**  
Future teams cannot understand or revise the rule.

**Prevention:**  
Rationale is mandatory.

---

## 7. No Alternatives Considered
Pretending the chosen solution was the only option.

**Why it’s harmful:**  
Hides trade‑offs and weakens review.

**Prevention:**  
Document rejected alternatives.

---

## 8. Contradictions with Existing Standards
New rules conflict with established ones.

**Why it’s harmful:**  
Creates ambiguity and governance debt.

**Prevention:**  
Reviewers must check compatibility.

---

## 9. Overly Technical Specifications
Embedding implementation details instead of enforceable rules.

**Why it’s harmful:**  
Limits flexibility and increases maintenance cost.

**Prevention:**  
Separate specification from implementation.

---

## 10. No Review Cycle
Standard is written as if permanent.

**Why it’s harmful:**  
Leads to outdated or harmful rules.

**Prevention:**  
Every standard must define a review cadence.
