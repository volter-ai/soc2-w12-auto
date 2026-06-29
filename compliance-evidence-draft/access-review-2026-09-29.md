# Access Review — Q3 2026 (interval ending 2026-09-29)

**Process:** User access recertification (quarterly)
**Criteria:** CC6.2 (Register/authorize/deprovision credentials), CC6.3 (RBAC / least-privilege / segregation of duties)
**Review date:** 2026-06-29
**Reviewer (EA):** automation (compliance-drafter)
**Status:** DRAFT — executive review required before signing

---

## Current collaborator snapshot

Fetched from GitHub API (`GET /repos/volter-ai/soc2-w12-auto/collaborators`) on 2026-06-29.

| # | User | Current Role | Current Permissions | Intended Role (per policy) | FLAG |
|---|------|-------------|---------------------|---------------------------|------|
| 1 | **BrunoCCPires** | `admin` | admin, maintain, push, pull, triage | maintainer / leadership | ⚠️ **Admin > needed role** — BrunoCCPires has admin-level access granting all permissions. Per the access-control-policy.md and control-matrix.md (C1/C2), access should be least-privilege with segregation of duties. If BrunoCCPires is the maintainer operating day-to-day controls, `write` or `maintain` is sufficient — admin grants `code:merge` which violates C2 (no actor holds `code:merge`). If BrunoCCPires is [OWNER] leadership accountable for the program, admin may be appropriate but should be documented and justified. |

**Total collaborators reviewed:** 1
**Flagged:** 1

### Non-collaborator note

- **yueranyuan** — contributed 1 commit (issue opener) but is **not a collaborator** on this repo. No access to remove. This is fine — external contributors submit via fork, or have org-level access.

---

## Intended role matrix (from access-control-policy.md)

The `compliance/policies/access-control-policy.md` is currently a **template with unset placeholders** (`[OWNER]`, `[DATE]`). It does not yet define an explicit user→role mapping for this repo. The policy states:

- **Least privilege**: agents run with capability-scoped tokens; no human/agent holds more access than their role requires.
- **Segregation of duties**: no actor holds both `code:propose` and `code:review`; no actor holds `code:merge`.
- **Branch protection**: main requires PRs + required checks; enforce_admins on.

The control-register.yml defines the following roles relevant to this repo's access:
- **maintainer** — operates day-to-day controls (process owner for access-review)
- **leadership** — accountable for the program, signs off
- **substrate** — manages infrastructure-level controls

**Observation:** The intended access matrix is not formally documented in the policy. The quarterly access-review procedure (risk register R9) is documented, but the mapping of who-should-have-what-role is implicit.

---

## Risk register relevance

- **R9 (Stale/over-privileged collaborator access)** — score 12 (treat). This review directly addresses R9. BrunoCCPires's admin perms should be confirmed as intentional or reduced.

---

## Anomalies summary

1. **Admin perms for BrunoCCPires** — exceeds least-privilege for a maintainer role. If the intent is maintainer, `write` or `maintain` (org-level) is sufficient. Admin grants `code:merge` capability, which conflicts with C2 (segregation of duties — no actor holds `code:merge`). However, admin may be appropriate for the org owner / leadership.

2. **Policy placeholders unfilled** — `access-control-policy.md` still has `[OWNER]` and `[DATE]` markers. The lack of a formal role matrix makes it harder to validate access against policy.

---

## Executive decisions needed

1. **Confirm BrunoCCPires's intended role** — is this person the maintainer (→ reduce to `write`/`maintain`) or leadership/owner (→ retain admin, but document exception for C2)?
2. **Fill the access-control-policy.md** with the actual owner and role-permission mapping.
3. **Sign the assertion** by editing the ledger artifact.

> **Note:** I (the EA) have not revoked any access — that is the executive's decision. This review surfaces what I found for your judgment.