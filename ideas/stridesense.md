# StrideSense
> Smartwatch gait patterns + medication effect ML + early warning for heart failure patients and payers

## The problem
Heart failure affects 6.5 million Americans and drives $30 billion in annual hospitalizations, with roughly 25% of patients readmitted within 30 days of discharge. The silent culprit is medication non-adherence: patients quietly skip diuretics, beta-blockers, or RAAS inhibitors, and the resulting fluid overload builds invisibly until an emergency admission. Current tools track only pill ingestion (smart dispensers, blister packs) — none can detect whether the medication's *physiological effect* is present, so a patient who swallows the pill but absorbs it poorly, or stops cold, looks identical until they crash.

## The solution
StrideSense runs as a background process on a patient's existing Apple Watch or Wear OS device, sampling raw accelerometer data continuously during natural daily ambulation — no dedicated sessions, no logging. A transformer model trained on labeled gait data from adherent versus non-adherent HF patients learns the characteristic biomechanical signature of fluid overload: shortened stride, reduced cadence variability, and a wider base of support that appear 48–72 hours before overt decompensation. When the model flags a sustained "non-medicated gait signature," it fires a single smart-home-style nudge to the patient and a dashboard alert to their remote care coordinator. The patient's experience is identical to not having the app.

## Why now
Apple HealthKit (2024) now exposes continuous high-frequency accelerometer streams to authorized third-party apps, and Apple Neural Engine inference runs a compact gait transformer at under 5% per-hour battery overhead — neither was feasible before 2023. Foundation model pretraining on large public gait datasets (UK Biobank accelerometry, NHANES) now enables clinical-quality transfer learning from as few as 300 labeled HF patient-weeks, compressing the data collection barrier that killed earlier wearable clinical tools.

## Who pays and why
Hospital systems pay because CMS penalizes HF readmissions under the Hospital Readmissions Reduction Program, costing the average health system $1–3M annually in withheld reimbursement — existing RPM programs (99453/99454 billing codes) already fund $150–300/patient/month for far weaker signal. Pharma companies running outcomes-based contracts for sacubitril/valsartan (Entresto, ~$3B revenue) need objective real-world adherence and effect data; StrideSense sells them a per-patient RWE feed. Revenue model: B2B SaaS per-patient-per-month to health systems + RWE data contracts with pharma.

## Scores
| Market | Feasibility | Clinical Impact | Regulatory | Author Score |
|:---:|:---:|:---:|:---:|:---:|
| 8 | 8 | 9 | 8 | 7 |

## Biggest risks
- Training the gait-to-medication-effect model requires a labeled clinical dataset from hospital partnership before any product exists, creating a cold-start dependency
- Apple Watch penetration in HF patients (median age 73, lower income) is currently ~15%, limiting addressable population until Android parity is built
- Pharma outcomes contract sales cycles run 12–18 months, compressing runway for the RWE revenue leg

## Pattern note
The prior high-scoring idea (AI Triage Bot) relied on active symptom input from patients — StrideSense directly inverts this by using a continuous passive biomechanical signal as a proxy for clinical state, targeting the same high-impact outcome (preventing avoidable clinical events) through zero user effort.
