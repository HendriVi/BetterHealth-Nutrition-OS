# BetterHealth Nutrition OS

A clinician-supervised precision nutrition platform for psychiatric clinics, private psychiatrists and metabolic-psychiatry programs.

## Current build

This repository currently contains a dependency-free interactive vertical-slice prototype with:

- English and German interfaces
- Clinician cohort dashboard and risk-prioritized review queue
- Structured clinical intake and hard safety constraints
- Longitudinal laboratory and treatment-domain views
- Constraint-based meal-plan presentation
- Gated ketogenic metabolic therapy workflow
- Combined psychiatric, metabolic, sleep and body-composition outcomes
- Versioned evidence register and traceable recommendation rationale
- Synthetic patient data only

Open `index.html` directly or serve the repository with any static web server.

## Clinical positioning

The product is designed as modular software. General education and wellness functions remain separate from clinician-controlled decision support. Ketogenic therapy, medication-aware recommendations and laboratory-driven treatment logic are treated as clinical modules requiring formal governance, validation and regulatory assessment before real-patient deployment.

## Product sequence

1. Validate workflow and design with synthetic cases.
2. Implement authenticated clinician and patient applications.
3. Add PostgreSQL, FHIR-compatible clinical records, audit logging and role-based access.
4. Implement deterministic safety rules and a constraint-based optimization service.
5. Add laboratory, wearable and food-composition integrations.
6. Conduct formal verification, usability testing, clinical validation and regulatory review.

See `docs/PRODUCT_SPEC.md`, `docs/CLINICAL_GOVERNANCE.md` and `docs/EVIDENCE_REGISTER.md`.
