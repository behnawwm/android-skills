---
name: android-code-review
description: Explicitly review an Android branch, commit or supplied worktree snapshot with a fresh subagent and matching source, returning local findings.
---

# Fresh local code review

Use only when explicitly requested or called by an explicitly invoked evaluation. Read the target project's instructions and the [run contract](../android-feature-eval/references/run-contract.md). Review results stay local.

## Resolve the target and policy

Accept a branch or commit for standalone review, for example `$android-code-review branch feature/search --base origin/main` or `$android-code-review commit abc1234`. These are agent-request arguments, not a shell command.

- Branch: resolve the requested ref and actual base from the request/parent-branch context or remote default branch. Compare `merge-base(base, target)..target`. Clarify an ambiguous base rather than assuming a branch naming convention.
- Commit: compare that immutable commit with its parent. A merge requires an explicit parent choice; a root commit uses the empty-tree comparison.
- Full-loop call: accept the parent's explicitly frozen `worktree_snapshot`, including intended committed/staged/unstaged/relevant untracked source. Record its base and fingerprint.

If a requested ref is missing, fetch the relevant ref when appropriate or report the blocker; never substitute HEAD. Standalone branch/commit review excludes unrelated worktree edits. Inspect matching source with `git show` or an isolated detached worktree; preserve the developer's checkout.

Use the project's designated review guide as the sole review how-to when available, preferably from the reviewed revision. Record the guide's path/revision and any fallback to the invoking checkout's copy. If the project has no guide, use the [bundled generic guide](references/review-guide.md) and explicitly record that choice. Do not combine conflicting severity/checklist policies.

## Dispatch a fresh reviewer

Use a new subagent without inherited implementation conversation, such as `fork_turns="none"` when supported. Supply only the actual requirements/specifications, immutable diff/base, matching frozen source, review-guide identity, applicable project instructions and available executed-check results. For a re-review, include prior findings/responses as evidence, without prescribing a conclusion.

Ask the reviewer to follow the selected guide, return findings locally and avoid source edits, installations, test-suite execution or platform comments. Do not supply implementer reasoning, leading suspected answers, credentials or raw sensitive captures. If independent subagents are unavailable, preserve the packet and mark the fresh-review gate blocked; same-context self-review is not independent.

## Record and return

Return the selected guide's findings and verdict. Record reviewer identity, fixed diff/source and guide identities, limitations and each finding's disposition: `confirmed`, `rejected_with_evidence`, `fixed_pending_verification` or `unresolved`. Re-review materially changed snapshots within the parent's budget.

When standalone, create a review-only private run record and follow [android-eval-learn](../android-eval-learn/SKILL.md). Do not imply device/unit gates ran. Clean only review-owned temporary resources. No commits, pushes or posted review comments are part of this skill.
