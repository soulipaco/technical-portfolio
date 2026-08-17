# Contact Center New-Hire Intelligence

[Repository](https://github.com/soulipaco/contact-center-new-hire-intelligence) · [Architecture](https://github.com/soulipaco/contact-center-new-hire-intelligence/blob/main/docs/architecture.md) · [Validation record](https://github.com/soulipaco/contact-center-new-hire-intelligence/blob/main/docs/validation_results.md)

## The problem

Contact-center leaders can usually see KPI values. The harder questions are whether a cohort is genuinely learning, whether apparent improvement is explained by handled volume, when performance is likely to reach a target, and which exceptions deserve action.

## What was built

The project maps four governed source tables into a Databricks product with:

- Bronze, Silver, and Gold analytical layers;
- cohort-level learning-curve candidates and governed winner selection;
- volume-aware diagnostics and process-control views;
- six-month Prophet scenarios;
- an AI/BI dashboard and Genie semantic surface;
- an optional action-planning workflow grounded in operating-playbook evidence;
- a configuration and build path for customer-shaped source tables.

## Decisions worth inspecting

- KPI direction, weighting, targets, and display behavior are explicit contracts rather than dashboard conventions.
- A generated adapter isolates customer column mappings from downstream analytics.
- Dashboard and Genie assets are stored with the repository instead of being treated as manual workspace configuration.
- Validation claims are recorded separately from guarantees about unseen customer data.

## Evidence

The `v1.0.0` release includes passing CI and local artifact-contract tests. The published validation record reports an independent customer-shaped rehearsal with 150,034 observations, 288 learning-curve candidates, 72 selected winners, 144 future forecast rows, 12 benchmark questions, and a nine-page dashboard. Those are release-validation results, not promises of business impact.

![Contact Center New-Hire Intelligence project overview](../assets/projects/contact-center-hero.png)

## Best next clicks

- [Five-minute quickstart](https://github.com/soulipaco/contact-center-new-hire-intelligence#five-minute-quickstart)
- [Data contracts](https://github.com/soulipaco/contact-center-new-hire-intelligence/blob/main/docs/data_contracts.md)
- [Acceptance matrix](https://github.com/soulipaco/contact-center-new-hire-intelligence/blob/main/docs/acceptance.md)
- [Privacy boundary](https://github.com/soulipaco/contact-center-new-hire-intelligence/blob/main/docs/privacy.md)

[Back to portfolio](../README.md)
