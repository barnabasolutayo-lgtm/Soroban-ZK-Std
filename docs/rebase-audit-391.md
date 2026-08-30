# Rebase Audit — Issue #391

**Date:** 2026-08-30  
**Audited by:** cybermax4200  
**Base branch:** `origin/main` @ `accbc7b3`

## Summary

All open branches were audited against the latest `main`. **No rebase is required.**

---

## Branch-by-Branch Findings

### 1. `fix/issue-389-remove-kani-dep`

| Property | Value |
|---|---|
| Unique commits | 1 |
| Merge base | `accbc7b3` (= current `main` HEAD) |
| Commits behind main | **0** |
| Conflicts | None |

**Verdict:** This branch is already based on the current `main` HEAD. A rebase would be a no-op. The branch is ready to merge as-is.

**Note:** This is the only open branch with actual pending work. It fixes two regressions introduced by PR #388:
- Removes unresolvable `kani = "0.45.0"` dev-dependency that breaks `cargo check` on `main`.
- Restores missing `fn` signatures for `mul_mod_with_overflow` and `mul_mod_naive` in `lib.rs`, fixing a self-recursive call.

---

### 2. `issue-364-halo2-primitives`

| Property | Value |
|---|---|
| Unique commits | 0 |
| Commits behind main | 21 |
| Already merged | Yes — PR #385 |

**Verdict:** This branch has no unique commits relative to `main`. Its work was fully merged via PR #385. No rebase needed; branch can be deleted.

---

### 3. `issue-371-fuzzing-infra`

| Property | Value |
|---|---|
| Unique commits | 0 |
| Commits behind main | 12 |
| Already merged | Yes — PR #383 |

**Verdict:** This branch has no unique commits relative to `main`. Its work was fully merged via PR #383. No rebase needed; branch can be deleted.

---

## Current `main` Build Status

`main` currently **fails to build** due to regressions from PR #388:

```
error: failed to select a version for the requirement `kani = "^0.45.0"`
candidate versions found which didn't match: 0.0.1, 0.0.0
```

**Fix:** Merge `fix/issue-389-remove-kani-dep` (PR #389) immediately to restore a green build.

---

## Recommended Actions

1. **Merge PR #389** (`fix/issue-389-remove-kani-dep`) — restores the build, no conflicts.
2. **Delete** `issue-364-halo2-primitives` and `issue-371-fuzzing-infra` — already merged, nothing left.
3. **Close issue #391** — rebase audit complete, no conflicts found across any open branch.
