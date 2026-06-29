## Decision brief — User access recertification (quarterly)
**Criteria:** CC6.2, CC6.3
**Owner (you):** maintainer

**What I did:** Ran the access-review playbook — queried GitHub API for all direct collaborators, compared current permissions against the access-control-policy's least-privilege/SOD requirements, and documented findings.

**Evidence:** [compliance-evidence-draft/access-review-2026-09-29.md](compliance-evidence-draft/access-review-2026-09-29.md)

**Findings / anomalies:**
- **1 collaborator reviewed**, **1 flagged**: BrunoCCPires holds **admin** (all perms including `code:merge`) — this exceeds what a maintainer role needs and conflicts with C2 segregation of duties (no actor holds `code:merge`). If BrunoCCPires is the org owner/leadership, admin may be appropriate but should be documented as an exception.
- **yueranyuan** is not a collaborator — no access to address (opened the issue from outside/some other access path).
- **`access-control-policy.md` still has template placeholders** (`[OWNER]`, `[DATE]`) — no explicit role→permission matrix is documented.

**Open items needing YOUR judgment / inputs only you can provide:**
1. Confirm BrunoCCPires's intended role — maintainer (→ reduce to `write`/`maintain`) or owner (→ retain admin, document C2 exception)?
2. Fill the `[OWNER]` and `[DATE]` placeholders in `access-control-policy.md`.
3. Edit the `assertion:` line in the ledger artifact to your own words, set `source: human-attested`, `assertion_author: <your login>`, `approver: <your login>`, then Approve.

**To sign:** edit the `assertion:` line in the ledger artifact to your own words, set `source: human-attested`, `assertion_author: <your login>`, `approver: <your login>` (+ attach any artifact-of-performance if applicable), then Approve. _I drafted this; the decision and the signature are yours._