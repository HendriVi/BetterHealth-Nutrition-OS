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
14. Ketogenic readiness, initiation and monitoring
15. Psychiatric and metabolic outcome tracking
16. Clinical alerts and escalation
17. Evidence register
18. Audit trail and plan versioning
19. Bilingual English/German interface
20. Clinical report export

## Architecture target

- Next.js / TypeScript clinician and patient applications
- PostgreSQL transactional database
- FHIR-compatible resource model for observations, conditions, medications, questionnaires, care plans and nutrition orders
- Deterministic rules service for contraindications, interactions, thresholds and escalation
- Mathematical optimization service for nutrient-constrained meal construction
- Separate generative-language service restricted to explanation, conversation and controlled substitutions
- Object storage for laboratory files and reports
- Immutable audit events
- EU or Swiss hosting

## Non-negotiable design principles

- Safety constraints override all optimization targets.
- Every recommendation exposes inputs, rationale, evidence grade, confidence, monitoring and stopping rules.
- Laboratory reference intervals, treatment thresholds and exploratory optimization targets remain distinct.
- Wearables are source- and device-specific trend measurements, not interchangeable diagnostic measurements.
- The system never creates a single universal health score.
- Real patient data are prohibited until privacy, security and clinical governance controls are implemented.
