---
name: android-feature-eval
description: Explicitly run a local Android feature evaluation with independent review, unit tests, ktlint, device verification, bounded repairs and persistent learning.
---

# Local Android feature evaluation

Use only when explicitly requested. One invocation coordinates the applicable steps; the developer need not invoke each supporting skill. Read the target project's repository instructions, the [run contract](references/run-contract.md) and task-relevant app context, if present. Paths such as `docs/agent-eval/` below belong to the evaluated project, not the skill installation.

## Run the loop

1. Establish the requirement, acceptance criteria and source scope. Include intended branch changes plus staged, unstaged and relevant untracked source. Use available structural tools or targeted search to identify affected modules and dependents. Do not substitute the last commit for a dirty worktree.
2. Create a private run record under the contract. Record the build/environment, device, source identity, allowed side effects and shared deadline/repair budget. Reuse session choices; clarify consequential unknowns while continuing independent preparation.
3. Follow [android-code-review](../android-code-review/SKILL.md), explicitly supplying a frozen `worktree_snapshot`, base and source fingerprint. Use a fresh subagent without inherited implementation conversation. Investigate findings and record each disposition separately from the reviewer output. An unavailable fresh reviewer is a missing gate.
4. Discover and run affected unit tests and the project's configured ktlint check tasks. Record commands, exit codes and actual coverage. Do not suppress failures or regenerate baselines to pass. If ktlint is not configured, record that gate as unavailable rather than installing it implicitly.
5. Follow [android-device-eval](../android-device-eval/SKILL.md) with the same run ID, acceptance criteria, source/build identity, environment/device and remaining budget.
6. Repair confirmed defects only within the authorized implementation scope. Observation-only requests do not authorize product repairs. After a source change, run affected checks, obtain fresh review for material changes, rebuild/reinstall and reverify affected device criteria. Earlier evidence does not prove the repaired source works.
7. Follow [android-eval-learn](../android-eval-learn/SKILL.md) after every attempt, before repair/retry, and at every controlled exit, including blocked or cancelled runs. Preserve earlier failures and self-contained app knowledge.

## Report

Return separate review, unit, ktlint and device outcomes; requirement-backed acceptance results; source/build/device identity; findings and dispositions; diagnostic limits; memory/report locations; and unresolved work. A feature failure can be detected by a correctly completed automation run. A partial run is not an overall pass.

This workflow does not start CI work, publish changes, generate navigation helpers or author E2E/regression suites. Evaluation alone does not authorize commit/push, toolchain installation or unrelated source edits. Use the package's setup guide only when setup is requested; do not depend on that guide being copied into the target app.
