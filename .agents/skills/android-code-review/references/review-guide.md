# Generic Android review guide

Use only when the target project has no designated review guide. Applicable repository instructions remain authoritative.

Review defects introduced by the supplied diff using matching source and actual requirements. Trace changed behavior through relevant callers, state, data mapping and lifecycle boundaries. Report actionable findings with a concrete triggering condition and consequence; distinguish demonstrated defects from missing context. Do not manufacture findings, enforce a quota or use an adversarial persona.

Where relevant, examine state restoration, lifecycle/cancellation, concurrency, error/loading behavior, UI/data contracts, resource ownership, permissions, sensitive data handling and work on the main thread. Read nearby code to establish impact; do not assume one architecture or framework. Mention missing evidence without claiming unexecuted tests passed or failed. Keep style-only preferences out unless project rules make them required.

For each finding provide severity, short title, changed-file location, trigger, impact and supporting evidence. Use:

- P0: widespread critical breakage requiring immediate action.
- P1: major malfunction with a concrete plausible trigger; fix before release.
- P2: meaningful defect with limited scope or circumstances.
- P3: minor actionable correctness issue.

Return `changes_requested` when actionable defects remain, `no_actionable_findings` when the available evidence supports that result, or `blocked` when missing context prevents a meaningful review. Include scope and limitations. `no_actionable_findings` is not proof of runtime correctness. Do not post to hosting platforms or modify the reviewed source.
