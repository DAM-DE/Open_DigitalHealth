# LiTrace
> Touchscreen micro-tremor from IMU during typing + personalized ML + lithium toxicity early warning for bipolar patients and psychiatrists

## The problem
Approximately 600,000 patients in Germany are managed on lithium for bipolar disorder — a medication with a therapeutic window so narrow (0.6–1.2 mmol/L) that toxicity causing irreversible renal damage and death can develop within hours of a dehydration event, drug interaction, or dose error. Monitoring consists of a blood draw every three months, leaving a 90-day blind window during which toxicity builds silently. No continuous passive monitoring solution exists outside hospital; patients are instructed to "watch for symptoms" — tremor, confusion, nausea — which are already markers of established toxicity, not early warning.

## The solution
LiTrace runs silently as a keyboard extension on the patient's existing iPhone (iOS 16+) or Android device. Every time the patient opens any app and types — a message, a search, a note — the extension captures the phone's accelerometer at 100 Hz for the duration of the typing session, entirely on-device without transmitting raw data. A personalized LSTM model learns each user's stable fine-motor typing signature over 14–21 days: their characteristic keystroke micro-vibration pattern, pressure distribution, and inter-key timing. When the model detects a sustained shift in the tremor-frequency band (8–12 Hz) relative to personal baseline across multiple sessions over 24–48 hours — the signature of emerging lithium toxicity — it fires a single alert to the patient ("Your typing pattern has changed — contact your psychiatrist today") and flags the deviation on the psychiatrist's monitoring dashboard. Conversely, a sustained reduction in typing dynamism below personal baseline can signal sub-therapeutic drift. The patient types exactly as they always have.

## Why now
On-device personalized time-series ML (Core ML 5 / TensorFlow Lite 2.13, 2023) can run a continuous tremor-detection model at under 2% battery overhead, with personalized calibration requiring only 2–3 weeks of natural typing — three years ago this required cloud compute and months of labeled data collection. iOS 16 (2022) enabled keyboard extensions to access Core Motion APIs with explicit user consent, providing the first legitimate continuous background IMU access pathway during typing events, a capability that did not exist before and is not reliant on specialized hardware.

## Who pays and why
German GKV statutory insurers pay because each lithium toxicity hospitalization costs €15,000–30,000 and lithium is a first-line GKV-covered maintenance therapy; DiGA Class IIa listing at €500–700/patient/year represents a clear ROI against even a 5% reduction in toxicity events among enrolled patients. Psychiatry practices billing under structured ambulatory care codes receive per-patient monitoring fees for enrolled lithium users. Pharma companies running outcomes-based lithium trials in maintenance bipolar and academic centers conducting pharmacovigilance need real-world side-effect trajectories; LiTrace licenses de-identified tremor data per patient-month as a secondary revenue stream. Revenue model: GKV DiGA reimbursement pass-through + psychiatrist SaaS subscription + pharma RWE data licensing.

## Scores
| Market | Feasibility | Clinical Impact | Regulatory | Author Score |
|:---:|:---:|:---:|:---:|:---:|
| 7 | 8 | 8 | 8 | - |

## Biggest risks
- The 8–12 Hz tremor signal of emerging lithium toxicity is subtle in early stages and is confounded by anxiety, caffeine, essential tremor, and other medications; a personalized deviation model partially mitigates this but false positives will erode psychiatrist trust without a rigorous noise-rejection layer
- iOS keyboard extension motion access requires an explicit user-granted motion permission during onboarding; low-tech or privacy-sensitive patients may decline, and this activation step is the primary drop-off risk
- Lithium prescribing is declining in some European markets as quetiapine and lamotrigine gain share; long-term TAM depends on expanding the platform to other narrow-therapeutic-index drugs (tacrolimus, phenytoin, carbamazepine) rather than remaining lithium-only

## Pattern note
Builds on the StrideSense/FlareCast pattern — personalized longitudinal baseline deviation detection for chronic disease — using an entirely new sensor access pathway (background IMU during keyboard extension) to monitor drug safety rather than disease activity, targeting Germany's lithium-managed bipolar population with a GKV toxicity-avoidance payer lever not previously covered.
