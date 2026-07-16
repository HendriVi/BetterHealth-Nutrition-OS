# Meal capture and diary import specification

## Purpose

Capture meals with the lowest practical user burden while preserving provenance, uncertainty and clinical safety.

## Supported entry methods

1. Photograph with patient confirmation
2. Barcode scan
3. Food and portion search
4. Saved meal or clinic recipe
5. Voice or written description followed by confirmation
6. CSV or JSON import from an existing diary
7. Manual clinician correction

## Photo workflow

### Vision proposal

The image service returns:

- Candidate food names
- Candidate preparation methods
- Candidate portion ranges
- Candidate hidden ingredients
- Per-item identification confidence
- Image-quality warnings

It does not return authoritative nutrient totals.

### Human confirmation

The patient confirms or edits:

- Food identity
- Portion or household measure
- Cooking method
- Added oils, sauces and sweeteners
- Brand or restaurant where relevant
- Whether the entire meal was consumed
- Meal date and time

### Database resolution

Each confirmed item is matched to a food-composition record. The stored meal item includes:

- Database and record identifier
- Database version
- Quantity and unit
- Edible portion
- Nutrient values per reference amount
- Conversion method
- Source confidence
- Patient-confirmed status
- Any clinician correction

### Clinical processing

Only resolved items enter:

- Nutrient-adequacy calculations
- Ketogenic carbohydrate accounting
- Allergy and intolerance checks
- Medication–food rules
- Sodium and fluid monitoring
- Energy and protein adherence
- Longitudinal treatment analysis

Unresolved or estimated items remain visible but are prevented from independently triggering clinical recommendations.

## Import architecture

All external diaries are mapped into a canonical import object:

```json
{
  "source": "csv|json|vendor",
  "source_record_id": "string",
  "occurred_at": "ISO-8601",
  "timezone": "Europe/Zurich",
  "meal_type": "breakfast|lunch|dinner|snack|other",
  "items": [],
  "source_confidence": "verified|mapped|estimated",
  "patient_confirmed": false
}
```

Imports must preserve the original payload for auditability while storing normalized records separately.

## YAZIO policy

The currently reviewed community repository is unofficial. BetterHealth will not use its shared credentials or reverse-engineered authentication in production. The supported first-stage migration path is patient-controlled export followed by CSV or JSON import. An API adapter requires an official agreement, documented scopes, privacy review and integration testing.

## Ketogenic accounting

Net carbohydrate is computed only when fibre and carbohydrate definitions are compatible with the source jurisdiction and database. The interface must display whether carbohydrate is total, available or net and retain the calculation rule.

Meal-level ketosis predictions are not shown as facts. Ketone response is measured separately and evaluated longitudinally alongside symptoms, sleep, medication, hydration and laboratory safety.

## Safety and privacy

- Meal photographs are sensitive health data when associated with a patient.
- Retention is configurable by clinic and consent version.
- The patient can review the source image and structured interpretation.
- Every correction creates an audit event rather than silently overwriting the prior interpretation.
- Eating-disorder risk can disable calorie-focused displays while preserving clinician monitoring.
- The system must support non-weight-loss goals and avoid compulsory daily weighing.
