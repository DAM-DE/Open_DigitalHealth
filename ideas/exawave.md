# ExaWave
> Overnight ambient acoustic fingerprint + longitudinal ML + COPD exacerbation prediction for GKV-enrolled patients

## The problem
COPD affects 6 million people in Germany and drives €6 billion in annual hospitalizations, with 50% of hospital costs concentrated in the 20% of patients who exacerbate repeatedly. Exacerbations are clinically detectable 7–14 days before hospitalization — audible as changes in wheeze, cough character, and breathing pattern — but patients and clinicians lack a real-world signal outside clinic walls. Current remote monitoring tools (pulse oximetry, symptom diaries) require daily patient action and catch deterioration too late.

## The solution
ExaWave runs as a background process on a patient's Android or iPhone placed on the nightstand. For 6–8 hours each night, an always-on acoustic model (running entirely on-device, no audio stored or transmitted) analyzes the composite overnight acoustic fingerprint: wheeze frequency and duration, cough character (wet vs. dry indicating bacterial vs. viral trigger), respiratory rate variability, and snoring pattern changes that correlate with mucus accumulation. A longitudinal transformer model tracks deviation from each patient's personal acoustic baseline over days — not single nights — and fires an alert to the supervising pneumologist when a 5-day trend crosses the exacerbation risk threshold, early enough for oral corticosteroid or antibiotic step-up rather than emergency admission. The patient does nothing: phone on nightstand, as always.

## Why now
On-device audio ML (Apple Core ML, Google AudioDecoder, MediaPipe Audio Classifier) can classify wheeze, cough subtype, and breathing pattern in real time at under 3% battery overhead — this was not achievable before 2023. Germany's DiGA fast-track (§139e SGB V) created a direct 12-month route to GKV reimbursement for apps showing clinical benefit in a prospective trial, and the DMP COPD program (800K enrolled patients) provides a pre-organized patient cohort with structured pneumologist relationships, removing the patient acquisition problem that kills most DTx startups.

## Who pays and why
German statutory health insurers (GKV: AOK, TK, Barmer) pay because COPD exacerbation hospitalizations cost €5,000–20,000 per admission and are a top DRG budget driver; DiGA reimbursement at €35–50/patient/month is trivially justified against avoided admissions. Pharma companies marketing maintenance inhalers (AstraZeneca Symbicort, Boehringer Ingelheim Spiriva) need real-world adherence and exacerbation-rate data for outcomes-based contracting; ExaWave sells them a de-identified RWE feed. Revenue model: DiGA-listed SaaS per-patient-per-month via GKV + pharma RWE data contracts.

## Scores
| Market | Feasibility | Clinical Impact | Regulatory | Author Score |
|:---:|:---:|:---:|:---:|:---:|
| 8 | 8 | 9 | 9 | - |

## Biggest risks
- Privacy: Patients and regulators may object to always-on overnight microphone; mitigation is on-device processing with no audio ever leaving the device, plus explicit informed consent with published data architecture
- Training data: Labeled overnight COPD acoustic datasets are sparse; initial model requires a university hospital partnership (Heidelberg Thoraxklinik or Charité) to collect 6–12 months of annotated recordings before product launch
- DiGA trial burden: The prospective clinical study required for DiGA listing demands €1–2M in bridge funding and 18+ months before reimbursement certainty, compressing runway

## Pattern note
Builds on the StrideSense pattern — passive continuous physiological monitoring via an ambient sensor to predict clinical deterioration before decompensation — but shifts from biomechanical (gait) to acoustic signal, from heart failure to COPD, and exploits the uniquely German DiGA/DMP infrastructure as both a regulatory fast-track and a go-to-market moat.
