---
name: android-device-eval
description: Explicitly verify an Android feature on a real device or emulator using ARTEMIS, diagnostics, bounded recovery and persistent learning.
---

# Complete local device evaluation

Use only when explicitly requested or called by `android-feature-eval`. Read the target project's instructions, the [run contract](../android-feature-eval/references/run-contract.md) and relevant app context. Standalone runs create their own record; parent calls inherit source identity, criteria, choices, deadline and remaining repair budget. Runtime paths belong to the target project.

## Prepare

1. Load only relevant durable feature notes and available recent failure summaries. Previous paths are hints, not verified current behavior. Learn the entry and feature without crawling the entire app.
2. Run `adb devices -l`. Honor the chosen device; otherwise use the sole authorized device. Ask when multiple targets or an ambiguity remain.
3. Discover ARTEMIS tools and actual schemas. On tool/start/device errors, call `mobile_diagnose` first, preferring supported safe self-healing. Follow ordered fixes and failed-task evidence before resubmitting. If the tool is unavailable, inspect MCP host logs and use the installed doctor's documented command. Settings changes may require restarting the MCP server. Report optional limitations rather than looping on them.
4. Verify variant/package, backend, locale, permissions, session, provider/data authorization and source identity. Do not infer the backend from a debug label. Reuse authorized existing login; consult ignored local context only when needed. Keep credentials out of prompts, captures and shared reports; stop on unexpected challenges. Follow only the target project's documented authentication rules.
5. Discover actual build/install commands through Android CLI or project metadata. Reuse an installed APK only with matching evaluated-source/build provenance; record hash and package/version. Preserve login/data. Do not wipe/uninstall as routine recovery. A changed source requires a new build for affected checks.

## Exercise and verify

Start private timestamped diagnostics before app navigation, including crash/system evidence that survives process restarts. Gather ANR/exit evidence where available. Verify debug HTTP capture or another authorized inspector before relying on network assertions; record unavailable probes. Redact to method/route/status and assertion-relevant fields before sharing.

Choose ARTEMIS mode for the task: Flash for direct reactive navigation with externally gathered evidence; Pro for exploration, persistent plans, diagnostics and verified checkpoints. Respect the installed version's capabilities. Give the exact device/package, actual prerequisites, goal, requirement-backed criteria, allowed actions, entry hints and deadline. Let the agent choose interactions rather than supplying an exhaustive tap script.

Poll status at least every minute, enforce the budget and inspect actual actions, screenshots and errors after completion. One controller per device: never race shell taps against the device agent. On stalls/errors, diagnose before recovery, preserve the attempt and stop when no actionable new diagnosis or budget remains. A minimal provider probe succeeding does not prove a full visual/tool request can complete.

Inspect the UI independently of the task's final claim. Compare displayed values and behavior with requirements and observed API data; task completion/HTTP200 alone is insufficient. Classify feature outcomes separately from automation/environment outcomes. Do not infer product failure from navigation failure alone, or automation failure from a correctly detected feature defect.

## Repair, learn and finish

Follow [android-eval-learn](../android-eval-learn/SKILL.md) after each attempt and before any retry/repair. Repair confirmed defects only within the user's implementation authorization; observation-only runs return findings. Source repairs require affected unit/ktlint checks, fresh review for material changes, rebuild/reinstall and device recheck. Return evidence invalidation to the parent orchestrator instead of starting another unbounded loop.

Always follow `android-eval-learn` before a controlled exit or handoff, including setup failures, cancellation, missing screens, exhausted budget or no new knowledge. On resume after interruption, check unfinished learning first. Save the blocked attempt before requesting external help. Developer corrections start as `user_report`; promote only after actual observation.

Keep private attempts under ignored `docs/agent-eval/runs/`, raw captures under ignored `.agent-eval/artifacts/`, and durable knowledge under `docs/agent-eval/flows/` indexed by `APP_CONTEXT.md`. Shared memory must not depend on local runs/artifacts. No navigation helpers, E2E/regression suites, QA handoffs or automatic policy edits.

Stop only run-owned tasks/diagnostics/tunnels and restore only temporary settings changed by the run. Report criteria/verdicts, automation outcome, source/APK/device/environment identity, diagnostic limits, available usage stats and evidence/memory locations. State untested areas. Finish after learning is saved, or explicitly report a persistence failure and the unsaved information.
