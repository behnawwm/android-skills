---
name: android-eval-learn
description: Explicitly preserve Android evaluation attempts and maintain cross-session app knowledge from observations and developer feedback.
---

# Persist evaluation learning

Use when explicitly requested or called by an explicitly invoked evaluation. Read the target project's instructions, relevant existing context and the [memory format](references/memory-format.md). This skill saves knowledge; it does not start another evaluation, install tools, contact others or generate test code.

## After every attempt

1. Read actual artifacts and source/build identities. Preserve original timestamps/revisions for older runs. Missing evidence stays missing; examples and a successful tool call are not verification.
2. Append a uniquely identified attempt to the private journal. Include expected versus actual behavior, criterion outcomes, automation status, classification, evidence limits, hypotheses and next action. Preserve failures/blocked attempts after later success. Use run/attempt IDs to avoid duplicate entries on repeated finalization.
3. Read the relevant feature note, deduplicate facts and promote useful observations with explicit provenance. Include date, source/build/environment/locale, validation status and revalidation trigger in the shared note itself. A navigation failure remains an automation limitation unless evidence establishes an app defect.
4. Save developer corrections as `user_report`, then add separate `device_observation` evidence if verified. Do not retroactively call a report verified or promote an untested recovery into a proven cause.
5. Update the durable app index only with self-contained feature-note links. Keep ignored runs, captures, machine paths and session dependencies out of shared knowledge. Apply routine memory updates locally; do not edit global instructions, skill policy, acceptance criteria or safety boundaries as automatic learning.

Use optional ignored `docs/agent-eval/APP_CONTEXT.local.md` only for authorized local credentials/settings, preserving existing entries with owner-only permissions. Never copy secret values into task prompts, shared notes or run reports. Use account aliases for outcomes.

On later runs, load only relevant durable knowledge and a few matching private summaries if available. Missing local history must not block understanding. Retain conflicting observations with their original conditions; mark facts stale after relevant changes. Semantic navigation hints support exploration; they are not executable replay scripts.

Return files changed, facts added or revalidated, unresolved gaps and evidence limits. No new confirmed fact is a valid outcome: still preserve the attempt. Report learning-write failures explicitly. Do not commit/push or generate QA handoffs, navigation helpers or E2E/regression suites.
