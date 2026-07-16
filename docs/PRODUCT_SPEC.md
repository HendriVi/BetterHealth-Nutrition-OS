# Product specification — BetterHealth Nutrition OS

## Intended users

- Psychiatric clinics
- Private psychiatrists
- Metabolic-psychiatry programs
- Clinical dietitians and nutrition professionals working under a defined care protocol
- Patients enrolled by an authorized clinic

## Initial protocols

### 1. Psychiatric cardiometabolic optimization

Target population: adults receiving psychiatric care with medication-associated metabolic risk, overweight or obesity, dysglycaemia, dyslipidaemia, hypertension, low diet quality or documented nutrient insufficiency.

Core loop: psychiatric state and medication → metabolic baseline → treatment-domain model → nutrient constraints → meal plan → adherence and adverse-event monitoring → repeat outcomes → clinician revision.

### 2. Clinician-supervised ketogenic metabolic therapy

Target population: selected adults for whom an appropriately governed clinic considers adjunctive ketogenic therapy. The module includes eligibility screening, contraindication and medication review, baseline measurements, initiation, stabilization, response evaluation, liberalization or discontinuation.

The software does not recommend medication withdrawal and does not interpret ketosis as proof of psychiatric efficacy.

### 3. Performance and body-composition optimization

Target population: clinically stable patients seeking high performance, improved energy availability, training recovery, body-composition change and cardiometabolic optimization. Safety and psychiatric stability remain higher-order constraints than performance objectives.

## User roles

- Clinic administrator
- Psychiatrist or prescribing clinician
- Dietitian / clinical nutrition professional
- Care coordinator
- Patient
- Read-only auditor / research role

## MVP functional domains

1. Clinic and user administration
2. Consent and privacy records
3. Patient identity, history and diagnosis
4. Medication and supplement reconciliation
5. Structured safety screening
6. Laboratory import with unit, method, date, fasting and confidence metadata
7. Wearable and patient-reported data ingestion
8. Treatment-domain state model
9. Objective ranking and conflict display
10. Nutrient and meal constraints
11. Deterministic recommendation rules
12. Clinician review, edit, reject and approval
13. Patient meal plan and substitutions
14. Photo-assisted meal capture with patient confirmation
15. Barcode, search, voice and manual food logging
16. Food-database provenance and source-confidence metadata
17. CSV and JSON import from existing food diaries
18. Ketogenic readiness, initiation and monitoring
19. Clinician-gated energy and macronutrient target calculator
20. Psychiatric and metabolic outcome tracking
21. Clinical alerts and escalation
22. Evidence register
23. Audit trail and plan versioning
24. Bilingual English/German interface
25. Clinical report export

## Meal capture architecture

A vision model may propose candidate foods, preparation methods and portion ranges. Its output is never the authoritative source of nutrient values.

The patient confirms ingredients, quantities, preparation and hidden ingredients. Confirmed items are resolved to approved food-composition records before they enter nutrient adequacy, ketogenic carbohydrate accounting, medication rules or treatment adaptation.

Unresolved meals remain labelled as estimates and cannot independently trigger clinical recommendations. Every correction creates an audit event.

## Food-data architecture

Initial source stack:

1. Swiss Food Composition Database
2. USDA FoodData Central
3. OpenFoodFacts for barcodes and branded products with explicit source-quality metadata
4. Clinic-verified recipes and portions
5. Licensed commercial recipe or restaurant data after review

Each item stores its database, version, identifier, quantity, unit, nutrient basis, conversion method and confidence.

## Existing-diary import

The initial migration route is patient-controlled CSV and JSON import into a canonical diary schema. The original payload is retained for auditability and normalized data are stored separately.

The reviewed community YAZIO repository is unofficial. BetterHealth does not use reverse-engineered authentication or publicly shared client credentials. A live YAZIO adapter requires an official permitted integration, security review and privacy assessment.

## Ketogenic target calculator

The calculator produces draft ranges, not prescriptions. Inputs may include age, sex, height, weight, body-fat estimate, activity, measured energy expenditure, energy adjustment, carbohydrate ceiling and clinic-configured protein parameters.

Production calculations must be versioned and retain their inputs, equation and uncertainty. Measured energy expenditure, kidney or liver constraints, pregnancy, eating-disorder risk, medication safety, energy availability and clinician judgement override calculated targets.

## Architecture target

- Next.js / TypeScript clinician and patient applications
- PostgreSQL transactional database
- FHIR-compatible resource model for observations, conditions, medications, questionnaires, care plans and nutrition orders
- Deterministic rules service for contraindications, interactions, thresholds and escalation
- Mathematical optimization service for nutrient-constrained meal construction
- Separate image-recognition service restricted to food proposals and uncertainty
- Separate generative-language service restricted to explanation, conversation and controlled substitutions
- Object storage for laboratory files, meal images and reports with clinic-configurable retention
- Immutable audit events
- EU or Swiss hosting

## Non-negotiable design principles

- Safety constraints override all optimization targets.
- Every recommendation exposes inputs, rationale, evidence grade, confidence, monitoring and stopping rules.
- Laboratory reference intervals, treatment thresholds and exploratory optimization targets remain distinct.
- Wearables are source- and device-specific trend measurements, not interchangeable diagnostic measurements.
- Model-generated nutrient estimates are never promoted to verified clinical data without confirmation and database resolution.
- Unofficial vendor credentials and reverse-engineered authentication are prohibited.
- The system never creates a single universal health score.
- Real patient data are prohibited until privacy, security and clinical governance controls are implemented.
