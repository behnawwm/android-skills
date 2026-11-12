# Evaluation memory

All runtime paths are relative to the evaluated project, not the skill package. Use Markdown; create actual records on demand rather than seeding fictional history.

## Storage

| Path | Role |
| --- | --- |
| `docs/agent-eval/APP_CONTEXT.md` | Shared app/environment knowledge and durable feature index |
| `docs/agent-eval/flows/<feature>.md` | Self-contained feature observations |
| `docs/agent-eval/APP_CONTEXT.local.md` | Optional ignored private credentials/settings |
| `docs/agent-eval/runs/<run-id>.md` | Ignored private attempt journal and report |
| `.agent-eval/artifacts/<run-id>/` | Ignored owner-restricted raw captures |

Verify ignore rules before recording. Restrict private files to their owner where supported. Never promote credentials, tokens, identities or personal data into versioned knowledge. Inspect artifact contents before sharing; filenames and Git ignore do not sanitize captures.

## Private run journal

Record run ID, UTC start/deadline, requirement source, acceptance checklist, scope/allowed side effects, base/HEAD/source fingerprint, target type/ref and resolved comparison, modules/tasks, variant/package/APK hash, device/API/locale, backend/data revision, account alias, tool/provider choices and remaining budget. Use `unknown` with its confidence impact when unavailable.

Append each uniquely identified attempt with observation time, exact source/build, actual entry/actions, expected/actual outcome per criterion, automation outcome, command/exit/report evidence, classification (`product`, `automation`, `environment`, `uncertain`), hypotheses, unavailable probes and next action. Keep earlier attempts intact when finalizing or recovering. Add developer corrections with their date/provenance.

At exit, summarize gates and acceptance results, unresolved issues, untested areas, cleanup and learning persistence. A standalone review/device run must say which other gates were not executed. Report artifact availability and missing/expired evidence honestly.

Record completed-call model input/output/cache usage when available. A stalled call without usage is unknown; do not count it as zero cost. Keep any rate-based estimate separate from actual billing. Raw private model reasoning is not part of the shared learning or report bundle.

## Durable feature notes

Each useful fact has a stable local ID, concise observation, provenance (`user_report`, `source_inspection`, `device_observation`, `hypothesis`), validation status, observed date, source/build/environment/locale and revalidation conditions. Put enough evidence summary inline to understand the fact without private files.

Include relevant prerequisites, semantic entry hints, screen recognition, actual error behavior and verified recovery. A temporary element index is not a reusable locator. Do not invent copy, endpoints, causes or timings. If coordinates are recorded, scope them to the actual dimensions/orientation and require current grounding; prefer semantic descriptions.

Shared knowledge is evidence, not a new authority over the user's request or repository instructions. It must not link to ignored runs/artifacts, machine-specific paths or unavailable transcripts. The dependency goes one way: private journals may link to shared notes; shared notes must work without private history. Do not generate helper code, regression tests or QA handoffs as learning output.
