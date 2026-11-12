# Shared local evaluation contract

Read for full-feature and standalone device evaluations. Runtime paths are relative to the target project. Skill references resolve from the installed sibling skill folders.

## Scope and budgets

Use one initial attempt plus at most two repair rounds and a 20-minute device-execution budget unless the developer chooses different limits. Record the starting time and deadline; child skills and retries inherit the remaining budget. Stop on success, cancellation, exhausted budget, repeated failure without an actionable new diagnosis, or an external prerequisite. Save learning before returning control.

Evaluation does not authorize clearing app data, uninstalling, destructive account actions, production transactions, uploads or publishing. Preserve existing login/data. Use an authorized test environment and provider for live screens. Resolve ambiguous device/environment choices before acting. Repair permission follows the actual task; observation-only runs remain observation-only.

Read the project's instructions and discover its actual architecture, variants and commands. Prefer Android CLI when available and ADB for targeting/diagnostics. Do not assume Gradle task names, SDK/JDK paths, package IDs, backend endpoints or login behavior.

## Run identity and storage

Choose a UTC timestamp, feature slug and unique suffix as the run ID. Use ignored `docs/agent-eval/runs/<run-id>.md` for private history and `.agent-eval/artifacts/<run-id>/` for owner-restricted raw captures. Before recording, verify ignore rules; merge missing entries without replacing existing rules. Ignore `docs/agent-eval/APP_CONTEXT.local.md` too. Git ignore alone does not protect file contents.

Use `docs/agent-eval/APP_CONTEXT.md` as the durable app index and `docs/agent-eval/flows/` for self-contained feature knowledge. Create minimal relevant context when needed; do not import unrelated app facts. Follow the [memory format](../../android-eval-learn/references/memory-format.md). Shared notes must not require ignored history, machine paths or unavailable transcripts.

Record base/merge-base, HEAD, evaluated-source fingerprint including intended uncommitted/untracked source, modules, actual tasks, variant/package, APK hash, requirements, device/API/locale, backend/data revision, account alias, tools/provider and budget. Mark unavailable values unknown. Exclude generated outputs and evaluation notes from the source fingerprint. Share one record between parent and children; avoid concurrent edits to it.

Keep credentials, personal data and raw captures out of shared knowledge and public reports. Inspect/redact before supplying diagnostics to a model or sharing artifacts. Record artifact availability and expiry; do not claim missing recordings exist.

## Review and deterministic checks

Resolve review refs to immutable commits. Branch review uses the merge-base with the actual target base; commit review uses its parent. Review matching target-version source. Worktree reviews must include intended staged, unstaged and relevant untracked changes and be labeled `worktree_snapshot`. Never silently review a different ref or mutate the developer's checkout to inspect it.

Discover JDK/SDK, module dependencies and build tasks. Run affected unit and ktlint checks; expand scope when shared contracts/build logic require it. Record command, source fingerprint, exit code and report. `NO-SOURCE`, skipped checks and absent tasks are not passing coverage. Formatting mutates source; inspect any authorized formatting change and rerun the check. Preserve unrelated work.

## Device evidence and verdicts

Start timestamped diagnostics before launch/navigation. Capture app plus crash/system evidence so a restart does not escape a PID-only filter. Record planned restarts separately. Gather ANR/process-exit evidence when available and report unavailable probes.

Use configured debug HTTP capture, an available inspector or other authorized network evidence; record method/route/status and only assertion-relevant fields. Debug logging may be unavailable. Missing logcat HTTP lines do not prove no request occurred. Source contracts identify expectations; observed traffic identifies actual behavior. Do not infer a cause from HTTP headers, model status or screenshots alone.

Judge each gate/criterion as `pass`, `fail`, `blocked`, `inconclusive`, `skipped` or justified `not_applicable`. Report automation status separately from feature status. HTTP 200 or task completion does not prove correct UI or business behavior. Compare visible values with actual response/requirements; without a scoring/business contract, UI/API consistency does not establish algorithm correctness.

For ARTEMIS, discover supported schemas/flags. Flash suits direct navigation and can use external diagnostics; Pro suits planning, exploration and verified checkpoints. Poll task status at least once per minute, inspect stored actions/screenshots and relevant errors after completion, and enforce the deadline. If a CLI-owned task is absent from MCP status, use its actual controller/logs and persisted history; do not interpret `unknown` as successful completion or queue a competing controller.

On failures, diagnose before retrying. HTTP200 response headers without a completed model response are not an executed UI action. A short health probe or a smaller goal succeeding does not isolate the original cause. Preserve the failed attempt before any changed-scope recovery. Count only completed-call token usage as known; missing usage is unknown, not free. Record model usage when available and label price estimates separately from billing.

Stop only run-owned controllers, diagnostics and tunnels. Restore only settings changed by this run. Source changes invalidate affected evidence and require rebuilding and rechecking. Never hide an earlier failure behind a later pass.

## Navigation knowledge

Keep relevant semantic entry hints as prose. Reuse them only after checking the current starting state, build, account, locale and expected destination. Reobserve after changed landmarks, unexpected screens or failed actions. Do not bypass the feature entry when that entry is under test.

Short familiar entry hints can reduce exploration; an exhaustive scenario list can bias the agent and obscure behavior. Give goals, acceptance criteria, invariants and allowed actions; let the device agent choose interactions. Do not write navigation-helper code or imply history replay re-executes actions. This workflow preserves knowledge without generating E2E/regression suites or QA handoffs.
