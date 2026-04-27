# NeuralTrace
> Passive smartphone kinematic fingerprint + longitudinal ML + pre-motor Parkinson's risk flagging for at-risk adults and pharma trial networks

## The problem
Parkinson's disease destroys 60–80% of dopaminergic neurons before the first clinical tremor appears; by diagnosis, neuroprotection is largely futile. Germany has 400,000 diagnosed patients and 20,000 new cases per year, but the economically and therapeutically critical population — the estimated 1–2 million in the prodromal phase — has no passive, continuous monitoring tool. Current prodromal screening (DaTscan, smell tests, REM sleep behaviour disorder questionnaires) requires specialist referral and active participation, and is used only in high-risk research cohorts, not at population scale.

## The solution
NeuralTrace runs silently as a background service on Android or iPhone, sampling the device gyroscope and accelerometer during events that happen naturally dozens of times per day: phone pickups, in-pocket walking, screen scrolling, and tap-typing. A personal-baseline transformer model extracts micro-kinematic features — sub-clinical resting tremor amplitude (4–6 Hz band power), movement smoothness (jerk cost), inter-tap interval variability, and pick-up trajectory asymmetry — and tracks their longitudinal drift against the user's own 30-day rolling baseline. No dedicated test, no active session; the phone is simply used as always. When a multi-week trend crosses a personalised risk threshold, NeuralTrace surfaces a single in-app message ("your movement patterns have shifted — consider discussing this with your GP") and, with opt-in consent, flags the user as a candidate for a pharma-sponsored prodromal trial.

## The evidence base
Multiple independent studies (MJFF mPower dataset, Arora et al. PLOS ONE 2015, Zhan et al. npj Digital Medicine 2022, Del Din et al. Brain 2021) demonstrate that kinematic irregularities from naturalistic phone interactions and free-living accelerometry predict Parkinson's diagnosis years before clinical onset with AUC 0.82–0.93; the PPMI longitudinal cohort confirms that these biomechanical signatures are detectable in prodromal participants classified by DAT-SPECT years prior to motor symptom onset. The mechanism is direct: substantia nigra degeneration disrupts basal ganglia–motor cortex timing circuits, producing measurable loss of movement smoothness and micro-tremor long before voluntary motor control is subjectively impaired.

## Why now
iPhone 14+ and Pixel 7+ gyroscopes (2022 onwards) have noise density below 0.003 dps/√Hz — a 4× improvement over 2020 hardware — sufficient for sub-threshold resting tremor detection that was previously only possible with clinical-grade inertial measurement units. Simultaneously, EMA conditionally approved alpha-synuclein–targeting therapies in 2024–2025 (and FDA priority review of neuroprotective agents is active), creating an urgent, massively funded pharma need for pre-symptomatic patients that simply did not exist three years ago: sponsors are paying $8,000–20,000 per enrolled prodromal participant.

## Who pays and why
Pharmaceutical companies running neuroprotective trials (Biogen/Denali BIIB122, Roche prasinezumab, AbbVie ABBV-0805) pay a per-referral or per-confirmed-enrolment fee — NeuralTrace is a patient-identification and pre-screening tool that dramatically cuts the €2,000–5,000 cost of recruiting a single prodromal participant via current academic methods. German GKV neurologists can bill for structured risk counselling in at-risk individuals (first-degree relatives of PD patients, ≈800,000 Germans) and pay a per-patient SaaS fee for the longitudinal dashboard. Long-term, a DiGA Class IIa listing targets €35–55/patient/month from statutory insurers as a digital health application for neurological risk monitoring, parallel to the Cara Care / Kalmeda DiGA template.

## Scores
| Market | Feasibility | Clinical Impact | Regulatory | Author Score |
|:---:|:---:|:---:|:---:|:---:|
| 9 | 8 | 9 | 8 | - |

## Biggest risks
- Pre-motor kinematic signal-to-noise requires large labelled longitudinal datasets (prodromal participants confirmed by DAT-SPECT); initial model accuracy depends on a data-sharing agreement with a university hospital (Charité, TU Munich Klinikum rechts der Isar) before commercial launch
- Psychological burden of a Parkinson's pre-symptomatic flag is significant — false positives can cause severe anxiety; requires careful clinical communication design and mandatory GP referral gate to avoid acting as an unqualified diagnostic tool
- Pharma enrolment revenue is episodic and tied to specific trial phases; pipeline risk means revenue could drop sharply between major trials, requiring DiGA reimbursement to be established as a parallel durable revenue leg

## Pattern note
Breaks the existing pattern of hospitalization-prevention in established chronic disease; instead introduces passive pre-diagnostic phenotyping in an apparently healthy population, with pharmaceutical trial enrollment as the primary initial revenue mechanism.
