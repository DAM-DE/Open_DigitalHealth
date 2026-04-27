# CogniMS
> Passive touchscreen interaction dynamics + personalized CNS behavioral model + MS relapse early warning for patients and neurologists

## The problem
Relapsing-Remitting Multiple Sclerosis (RRMS) affects 800,000 Europeans — predominantly women aged 20–40 — and drives 1–2 relapses per year despite disease-modifying therapy, each costing €8,000–25,000 in acute treatment and carrying risk of permanent disability accumulation. The 72-hour window for high-dose corticosteroids to shorten relapse duration and reduce disability progression is routinely missed because patients self-report symptoms only after days of denial or normalization, and neurologists have no real-world signal between 6-monthly clinic visits. Existing digital MS tools are symptom diaries or fatigue scales — all active, all under-reported, all too slow.

## The solution
CogniMS installs once as a keyboard extension (iOS) or accessibility-layer monitor (Android) and thereafter runs entirely in the background. It passively captures four streams during normal daily phone use: inter-key interval variance and backspace rate from typing (corticospinal tract motor dexterity), swipe/scroll velocity consistency and touchscreen pressure distribution (cerebellar fine motor coordination), ambient accelerometer gait signatures during walking, and screen-session length as a proxy for cognitive fatigue. A personalized on-device transformer model learns each patient's unique baseline over the first 3–4 weeks, then tracks multi-day deviations. When three or more consecutive days exceed the patient's personal threshold across two or more channels, it fires one push notification — "Your movement patterns have changed over the past 3 days — consider calling your neurologist today" — and sends a flagged alert to the treating neurologist's dashboard. All inference runs on-device; no raw interaction data is ever transmitted or stored externally.

## The Clinical Evidence
New demyelinating lesions reduce axonal conduction velocity in motor and cerebellar pathways before the patient consciously registers weakness or numbness, making fine motor behavior a leading biomarker of MS relapse onset. A 2020 NPJ Digital Medicine paper (Creagh et al., Oxford/Biogen) demonstrated that passive smartphone accelerometer and touchscreen interaction data predicted 85% of MS relapses before clinical self-report, with a median lead time of 3.8 days; a 2022 Neurology paper further validated that automated finger-tapping speed deteriorates measurably in the 72–96 hours before patient-reported symptom onset, aligning with the corticosteroid intervention window.

## Why now
On-device transformer inference (Apple Core ML 3, Android NNAPI) now runs a personalized 4-channel time-series model at under 3% hourly battery overhead — infeasible before 2023. Federated learning frameworks allow CogniMS to improve its relapse-detection model across thousands of patients without any raw behavioral data leaving individual devices, a privacy architecture that was not productizable at scale until 2024.

## Who pays and why
German GKV reimburses DiGA-listed apps for MS under §139e SGB V at €400–800/patient/year — preventing a single relapse hospitalization (€8,000–25,000) generates 10–30× ROI for the insurer relative to the DiGA subscription cost. Biogen (Tysabri, Fampyra), Novartis (Kesimpta), and Roche (Ocrelizumab) all operate outcomes-based contracts for DMTs and need real-world relapse-rate reduction evidence; CogniMS provides a de-identified per-patient RWE feed under pharma data licensing agreements. Neurology practices in Germany receive structured DMP billing per enrolled patient, creating an aligned incentive for the prescribing neurologist to onboard their RRMS panel.

## Scores
| Market | Feasibility | Clinical Impact | Regulatory | Author Score |
|:---:|:---:|:---:|:---:|:---:|
| 8 | 8 | 9 | 7 | - |

## Biggest risks
- Keyboard extension permission anxiety: patients and regulators are acutely suspicious of any app that monitors typing; mitigated by on-device-only processing, published data architecture, and open-source inference code
- Cold-start labeling dependency: training the personalized relapse model requires confirmed relapse labels (neurologist-diagnosed + MRI-supported), demanding a clinical partnership before commercial launch and adding 12–18 months to the timeline
- MS relapse phenotype heterogeneity: cerebellar relapses (balance/coordination) produce a different signal profile from spinal cord relapses (limb weakness) or optic neuritis (no motor signal at all) — a single model may underperform across phenotypes without explicit stratification

## Pattern note
Extends the StrideSense/FlareCast pattern — continuous passive behavioral signal predicting costly clinical events before they become irreversible — into a CNS inflammatory disease using touchscreen dynamics as a novel signal modality not present in any prior portfolio idea.
