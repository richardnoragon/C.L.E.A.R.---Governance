CLI design: clearctl (lifecycle automation)

### 5. CLI design: `clearctl` (lifecycle automation)

High‑level design for a future CLI tool; save as `clearctl/README.md` or `docs/clearctl.md`:

```md
# clearctl – C.L.E.A.R. Governance CLI

`clearctl` is a conceptual CLI for automating common governance lifecycle tasks:
creating standards, running checks, and managing reviews.

---

## Core Commands

### 1. `clearctl init`
Initialize governance structure in a repo.

- Creates baseline directories (`roles/`, `templates/`, `lifecycle/`, `anti-patterns/`, `enforcement/`, `adoption/`, `review-cycles/`, `docs/`)
- Optionally runs the bootstrap script.

Example:

```bash
clearctl init
```

---

### 2. `clearctl standard new`

Scaffold a new standard from `STANDARD_TEMPLATE.md`.

```bash
clearctl standard new --id STD-001 --name logging-standard --title "Logging Standard"
```

Behavior:

- Creates `standards/STD-001-logging-standard.md`
- Fills metadata (ID, title, status: Draft)
- Optionally assigns Author and Steward.

---

### 3. `clearctl standard status`

Show lifecycle status of standards.

```bash
clearctl standard status
```

Outputs a table:

- ID, Name, Status (Draft / In Review / Approved / Enforced / Adopted / Under Review / Deprecated)
- Steward, Next Review Date.

---

### 4. `clearctl review start`

Start a Legitimize review for a standard.

```bash
clearctl review start --id STD-001 --reviewers alice,bob --steward carol
```

Behavior:

- Creates a review file from `templates/REVIEW_TEMPLATE.md`
- Links the standard
- Records reviewers and steward.

---

### 5. `clearctl review close`

Close a review with a decision.

```bash
clearctl review close --id STD-001 --decision "Approve with Changes" --summary "…" 
```

Behavior:

- Updates the review file with decision and rationale
- Updates standard status
- Optionally opens follow‑up tasks (e.g., enforcement spec).

---

### 6. `clearctl enforce spec`

Scaffold an enforcement specification.

```bash
clearctl enforce spec --id STD-001 --owner dora
```

Behavior:

- Creates `enforcement/specs/STD-001-enforcement.md` from `ENFORCEMENT_SPEC_TEMPLATE.md`.

---

### 7. `clearctl adopt plan`

Create migration and rollout skeletons.

```bash
clearctl adopt plan --id STD-001 --team "payments"
```

Behavior:

- Creates a migration guide in `adoption/MIGRATION_GUIDES/`
- Creates a rollout plan in `adoption/ROLLOUT_PLANS/`.

---

### 8. `clearctl review-cycle schedule`

List upcoming reviews.

```bash
clearctl review-cycle schedule
```

Reads `review-cycles/SCHEDULE.md` (or a machine‑readable file) and prints upcoming review dates.

---

## Implementation Sketch

- Language: Go, Rust, or Python (your choice)
- Config: `clearctl.yml` in repo root (paths, defaults, roles)
- Operates purely on files in the repo (no external services required)
- Designed to be CI‑friendly (e.g., `clearctl validate` for governance checks)

---

This gives you a clear blueprint if you ever want to actually implement `clearctl` as a real tool.