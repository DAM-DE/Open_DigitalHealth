# FlareCast
> Wrist temperature deviation + HRV + sleep fragmentation → IBD flare prediction 48–96h early for patients and gastroenterologists

## The problem
Inflammatory bowel disease (Crohn's and ulcerative colitis) affects 6.8 million Europeans and costs the healthcare system €12–20B annually, driven largely by unpredictable flares that escalate to hospitalisation (€8,000–15,000 each) or surgery. Patients on biologics (adalimumab, vedolizumab, ustekinumab — €15–30K/year/patient) have no real-time feedback between 6-monthly colonoscopies; by the time they feel a flare, the inflammatory cascade is already advanced. Current remote monitoring options are either active (symptom diary apps, stool calprotectin home tests) or require blood draws — none are invisible, continuous, or predictive.

## The solution
FlareCast runs silently on the patient's existing Apple Watch (Series 8+) or Samsung Galaxy Watch 6+, reading three streams the device already captures: wrist skin temperature, HRV, and sleep fragmentation. During an IBD flare, pro-inflammatory cytokines (IL-6, TNF-α) elevate systemic temperature by 0.3–0.8°C above personal baseline 24–96 hours before overt gastrointestinal symptoms — a signal measurable at the wrist with the 2022-era continuous temperature sensor. A personalised transformer model learns each patient's baseline thermal-autonomic pattern and flags sustained deviations; when the combined signal crosses threshold, it sends a single push to the patient ("your pattern suggests a possible flare in 2–3 days — contact your IBD nurse") and a dashboard alert to their gastroenterology team. The patient does nothing differently on any given day.

## Why now
Apple Watch gained a continuous wrist temperature sensor in September 2022 (Series 8) and exposed it to third-party HealthKit apps in watchOS 9 — this did not exist three years ago. Simultaneously, transformer models for irregular clinical time-series now achieve clinical-grade sensitivity on datasets as small as 400 patient-years, collapsing the data volume barrier that previously made personalised wearable disease monitoring impractical.

## Who pays and why
German statutory health insurers (GKV) reimburse certified digital therapeutics via the DiGA fast-track pathway at €400–800/patient/year — FlareCast targets DiGA Class IIa approval, following the template of Cara Care (IBD coaching, approved 2021). AbbVie, Takeda, and Pfizer need real-world evidence of biologic durability for outcomes-based contracts; FlareCast sells a per-patient RWE feed to pharma in parallel. Longer term, gastroenterology practices in Germany receive €130–210 per quarter per enrolled patient under structured disease management billing codes (DMP). Revenue model: B2B SaaS per-patient-per-month to clinics + GKV reimbursement pass-through + pharma RWE data licensing.

## Scores
| Market | Feasibility | Clinical Impact | Regulatory | Author Score |
|:---:|:---:|:---:|:---:|:---:|
| 8 | 7 | 8 | 7 | - |

## Biggest risks
- Apple Watch Series 8+ penetration in the IBD population (median age 35–45, mixed income) is currently ~20–25%, creating an addressable subset; Galaxy Watch parity reduces but does not eliminate this gap
- Cold-start data problem: training the personalised flare model requires 6–12 weeks of baseline data per patient plus confirmed-flare labels, necessitating a clinical partnership before commercial launch
- Wrist temperature is a distal proxy for core temperature; individual variation in vasomotor tone (cold hands, exercise, ambient temperature) will generate false positives that erode clinical trust without a robust noise-rejection layer

## Pattern note
Extends the StrideSense pattern — continuous passive wearable signal as proxy for disease activity, targeting avoidable costly clinical events — to a younger, smartphone-native patient population using a different sensor modality (thermal) that became hardware-accessible only in 2022, with a clearer EU reimbursement pathway (DiGA) as the primary commercial entry point.
