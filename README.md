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
- Photo-assisted meal-capture specification
- Patient confirmation of foods, portions and preparation
- Food-database provenance and confidence states
- Existing-diary CSV and JSON import architecture
- Clinician-gated energy and ketogenic macronutrient calculation design
- Synthetic patient data only

Open `index.html` directly or serve the repository with any static web server.

## Source-integration policy

The image-recognition workflow was informed by the FoodNutrition-AI proof of concept, but BetterHealth does not accept model-generated nutrient totals as clinical data. Computer vision proposes foods and portions; the patient confirms them; confirmed items are resolved against approved composition databases before clinical rules run.

The reviewed YAZIO repository is an unofficial API description. BetterHealth will not embed reverse-engineered authentication or public client credentials. Patient-controlled CSV and JSON import is the initial migration route.

The `awesome-nutrition-tracking` catalogue is used to identify useful product patterns and candidate services. The planned core food-data stack is the Swiss Food Composition Database, USDA FoodData Central and OpenFoodFacts with source-quality metadata.

The KetoDiet calculator project is GPL-3.0. BetterHealth adopts relevant user-input and warning concepts but uses an independently implemented calculation engine rather than copying GPL code into the proprietary clinical product.

## Clinical positioning

The product is designed as modular software. General education and wellness functions remain separate from clinician-controlled decision support. Ketogenic therapy, medication-aware recommendations and laboratory-driven treatment logic are treated as clinical modules requiring formal governance, validation and regulatory assessment before real-patient deployment.

## Product sequence

1. Validate workflow and design with synthetic cases.
2. Implement authenticated clinician and patient applications.
3. Add PostgreSQL, FHIR-compatible clinical records, audit logging and role-based access.
4. Implement deterministic safety rules and a constraint-based optimization service.
5. Add laboratory, wearable and food-composition integrations.
6. Conduct formal verification, usability testing, clinical validation and regulatory review.

See:

- `docs/PRODUCT_SPEC.md`
- `docs/CLINICAL_GOVERNANCE.md`
- `docs/EVIDENCE_REGISTER.md`
- `docs/OPEN_SOURCE_INTEGRATION_REVIEW.md`
- `docs/MEAL_CAPTURE_AND_IMPORT_SPEC.md`
