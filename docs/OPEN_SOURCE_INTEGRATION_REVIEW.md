# Open-source and external nutrition integration review

Reviewed: 16 July 2026

## Governing principle

BetterHealth Nutrition OS may reuse interaction patterns, standards and permissively licensed components, but clinical nutrient values must come from traceable food-composition records and deterministic calculations. A vision or language model may propose foods, portions or corrections; it may not become the source of record for nutrient quantities, contraindications or treatment decisions.

## FoodNutrition-AI

Useful workflow concepts:

- Meal photograph upload
- Explicit meal date and time
- Patient goal and contextual description
- A refinement step after the initial image analysis
- Macronutrient and micronutrient display
- Longitudinal meal history

Changes required for BetterHealth:

1. Computer vision returns candidate foods, candidate portions and uncertainty.
2. The patient confirms ingredients, portions, preparation method and hidden ingredients such as oils.
3. Confirmed items are resolved against the Swiss Food Composition Database, USDA FoodData Central or an approved branded-food source.
4. Clinical rules run only after database resolution.
5. Unconfirmed entries remain labelled as estimates and cannot independently trigger treatment changes.
6. Images are governed by clinic-configurable retention and deletion rules.

The original proof of concept asks a generative model to estimate nutrient values directly and supports clinical goal categories without a medical safety layer. That approach is unsuitable for a clinic-grade product.

## saganos/yazio_public_api

This repository documents an unofficial YAZIO interface and includes reverse-engineered authentication examples. It is not an acceptable production dependency for patient data because the integration is not an official contracted interface and the repository discusses shared client credentials.

BetterHealth implementation:

- Support patient-controlled CSV and JSON diary import.
- Build a canonical food-diary import schema with source, timestamp, units, database identifiers and confidence.
- Keep a YAZIO adapter disabled unless an official, contractually permitted integration becomes available.
- Never embed credentials taken from a public repository.

## awesome-nutrition-tracking

Use this catalogue as a discovery map rather than a dependency. It identifies useful product patterns and potential services:

- Photo logging
- Barcode scanning
- Offline and privacy-focused diaries
- Recipe parsing
- Meal-plan editing
- Food and restaurant databases

Initial BetterHealth data stack:

1. Swiss Food Composition Database for Swiss reference foods
2. USDA FoodData Central for broad reference coverage
3. OpenFoodFacts for barcode and branded-product discovery, with explicit source-quality metadata
4. Clinic-verified recipes and portion definitions
5. Optional commercial recipe or restaurant adapters after licensing review

## ketodiet/keto-calculator

The project contains useful interaction and warning concepts: age, sex, height, weight, body-fat estimate, activity, carbohydrate limit, energy adjustment, lean-mass-related protein calculation and warnings for implausible outputs.

The source is GPL-3.0. BetterHealth therefore does not copy its implementation into a proprietary product. The prototype uses independently implemented standard equations and labels every result as a draft requiring clinical review.

Production requirements:

- Support measured resting energy expenditure when available.
- Store the equation, version, inputs and output uncertainty.
- Separate estimated energy expenditure from prescribed energy intake.
- Apply renal, hepatic, pregnancy, eating-disorder, medication and energy-availability constraints.
- Prevent activation while ketogenic safety blockers remain unresolved.

## Keto Cycle review repository

The supplied repository could not be verified during this review and appears to be promotional content rather than a dependable software or clinical source. No code, claims or diet rules were incorporated.

## Prototype v0.8 additions

- Photo-assisted meal capture
- Patient confirmation of foods and portions
- Database provenance labels
- Estimated-versus-confirmed meal states
- CSV/JSON diary import architecture
- Explicit restriction on unofficial YAZIO integration
- Clinician-gated ketogenic energy and macro calculator
- Source review displayed in the evidence register
