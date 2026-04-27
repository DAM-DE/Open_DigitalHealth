# CognaTap
> Passive smartphone typing dynamics + longitudinal ML + covert hepatic encephalopathy prediction for cirrhosis patients and GKV payers

## The problem
Liver cirrhosis affects ~250,000 people in Germany and ~5 million across the EU; an estimated 30–40% carry covert hepatic encephalopathy (cHE) at any given time — subtle cognitive-motor impairment that is clinically invisible until it escalates to an overt HE episode (confusion, stupor, coma) requiring emergency hospitalisation at €8,000–15,000 per admission. Patients on first-line rifaximin prophylaxis still experience breakthrough episodes, and the only validated screening tool (the EncephalApp Stroop test) requires a dedicated clinic visit and trained staff — performed at most quarterly, leaving months of blind drift. There is no continuous, between-visit signal.

## The solution
CognaTap runs as a background accessibility-layer service on Android (and an iOS custom keyboard extension) on the patient's existing smartphone, capturing only typing-dynamics metadata — inter-keystroke interval, key hold duration, backspace frequency, and touch-tap latency — from natural daily phone use, with zero content access and all computation on-device. During emerging cHE, slowed psychomotor processing and reduced fine motor accuracy manifest as measurable shifts in these timing signals: longer latencies, higher error-correction rates, and increased variability in tap duration — the equivalent of a continuous passive Stroop test running 24 hours a day, 7 days a week. A personalised LSTM model establishes each patient's individual typing baseline over the first 14 days, then monitors for sustained 7-day deterioration trajectories, firing a single dashboard alert to the supervising hepatologist: "Patient X's cognitive-motor pattern has deteriorated 28% over 7 days — consider ammonia check or rifaximin adjustment." The patient experiences nothing: no app to open, no tests to perform.

## Why now
Android's Accessibility Service API and iOS's custom keyboard framework have both, since 2022–2023, enforced strict on-device processing constraints and explicit consent flows that make passive keystroke dynamics collection GDPR-compliant without content capture — the legal and technical infrastructure to do this safely at scale simply did not exist three years ago. Simultaneously, edge-compute LSTM inference on 2022+ flagship chips (Snapdragon 8 Gen 2, Apple A16) now runs personalised time-series anomaly detection at under 2% daily battery overhead.

## Who pays and why
German statutory health insurers (GKV) pay because each avoided overt HE hospitalisation saves €8,000–15,000, and the cirrhosis DRG group is a top-20 budget line in every major Krankenkasse — DiGA Class IIa listing (ICD K72/K76.6) at €400–700/patient/year is trivially ROI-positive after one avoided admission. Alfasigma (rifaximin/Xifaxan), whose European generic competition intensified in 2024, needs real-world evidence showing rifaximin's cHE-suppression durability to defend outcomes-based formulary positions; CognaTap sells a de-identified per-patient RWE feed tied directly to the drug's mechanism. Revenue model: DiGA-listed SaaS per-patient-per-month via GKV + pharma RWE data licensing to Alfasigma and Norgine.

## Scores
| Market | Feasibility | Clinical Impact | Regulatory | Author Score |
|:---:|:---:|:---:|:---:|:---:|
| 8 | 8 | 9 | 9 | - |

## Biggest risks
- Privacy optics: Keystroke monitoring is politically sensitive in Germany even with zero content capture; transparent on-device architecture and patient advocate co-design are non-negotiable for adoption
- Training data cold-start: Requires a hepatology partnership (e.g., Charité Hepatology, Hamburg UKE) to collect labelled typing + confirmed HE episode data from ~200 cirrhosis patients before the personalised model can be validated
- Addressable population cap: Only cirrhosis patients with sufficient daily smartphone typing yield a usable signal — estimated at 80–100K in Germany — capping near-term GKV revenue unless expanded to broader chronic liver disease (NAFLD-cirrhosis pipeline)

## Pattern note
Extends the StrideSense pattern — continuous passive sensor signal as proxy for disease-state deterioration, targeting an avoidable high-cost hospitalisation — but shifts from biomechanical (gait) to cognitive-motor (typing dynamics), from heart failure to hepatic encephalopathy, exploiting a sensor stream (keyboard metadata) that became legally and technically capturable only post-2022.
