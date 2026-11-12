# Android skills

Optional, local Android feature evaluation with fresh code review, unit tests, ktlint, ARTEMIS device verification and persistent learning.

| Skill | Purpose |
| --- | --- |
| [android-feature-eval](.agents/skills/android-feature-eval/SKILL.md) | Coordinate the complete loop, bounded repairs and learning |
| [android-code-review](.agents/skills/android-code-review/SKILL.md) | Review a branch, commit or supplied worktree snapshot with a fresh subagent |
| [android-device-eval](.agents/skills/android-device-eval/SKILL.md) | Run the complete device workflow independently |
| [android-eval-learn](.agents/skills/android-eval-learn/SKILL.md) | Preserve attempts and maintain reusable app knowledge |

The feature orchestrator calls review, checks, device evaluation and learning. Device evaluation always calls learning, including after blocked or failed attempts. Each skill can also be requested independently. These are agent instructions, not a separate executable test runner.

## Install

Ask your coding agent:

> Install the four skills from https://github.com/behnawwm/android-skills into this project's `.agents/skills/`, preserving their sibling layout and bundled references. Reuse existing installations. If my client uses another skill discovery directory, link these four folders there from `.agents/skills/` without overwriting existing skills. Follow the repository's SETUP.md to prepare missing tools. Do not start an evaluation yet.

The canonical skills live in `.agents/skills/`. They use the [Agent Skills format](https://agentskills.io/specification); discovery and invocation syntax depend on your client. Codex metadata preserves explicit-only invocation. Other clients should be configured for manual invocation where supported. The instructions themselves require an explicit request.

Keep all four skills together: their shared references are part of the package. Client links should point to individual skill folders so unrelated installed skills are preserved.

## Use

Example requests, using Codex-style skill names:

```text
Use $android-feature-eval for my current feature changes against origin/main.
Use the stagingDebug variant on emulator-5554. Verify the acceptance criteria
in the feature description; keep the existing login.

Use $android-code-review branch feature/search --base origin/main.

Use $android-code-review commit abc1234.

Use $android-device-eval to verify the settings feature on emulator-5554.
```

Supply the feature goal, acceptance criteria and any known device/build/environment choices. The agent discovers actual Gradle tasks and module scope. No particular module architecture, backend, package name, review policy or login behavior is assumed.

Defaults: one initial attempt plus at most two repair rounds and a 20-minute device budget. Change these in your request. A completed automation task and a passing feature are separate results; HTTP 200 does not prove correct behavior.

## Project knowledge

Use [the blank app-context template](templates/APP_CONTEXT.md) when adding this workflow to a project. Project-specific facts belong in that project's context, not in these reusable skills.

| Location in the target project | Contents |
| --- | --- |
| `docs/agent-eval/APP_CONTEXT.md` | Shared app/environment knowledge and feature-note index |
| `docs/agent-eval/flows/` | Self-contained observed behavior, provenance and revalidation hints |
| `docs/agent-eval/APP_CONTEXT.local.md` | Optional ignored local accounts/settings; owner-only permissions |
| `docs/agent-eval/runs/` | Ignored local attempt journals and reports |
| `.agent-eval/artifacts/` | Ignored private screenshots, logs, recordings and diagnostic captures |

Add the private paths to the target project's ignore rules before recording anything. Shared knowledge must remain understandable when all local run files are absent. Secrets and personal data stay out of shared notes and published artifacts.

The workflow records navigation knowledge as prose. It does not generate navigation helpers, Appium/Playwright suites, QA handoffs or CI jobs. It does not commit, push or publish changes as an evaluation side effect.

## Setup

See [SETUP.md](SETUP.md) for the short Android CLI and ARTEMIS setup prompt. An authorized Android device or running emulator, the project's JDK/SDK, and an ARTEMIS model provider are required for device evaluation. An independent subagent is required for the fresh-review gate.

## License

[MIT](LICENSE). Android CLI and ARTEMIS are separate projects with their own licenses and setup requirements.
