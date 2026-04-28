# ProdroSense
> Passive smartphone behavioral fingerprint + personalized drift model + psychotic relapse prediction for schizophrenia patients and community psychiatry teams

## The problem
Schizophrenia affects approximately 800,000 people in Germany, with 60,000–80,000 psychiatric hospitalizations annually at a cost of €12,000–35,000 per episode. The two-week prodromal window before a psychotic break — characterized by social withdrawal, disrupted sleep, and erratic communication patterns — is clinically detectable in retrospect but invisible to community psychiatry teams between monthly appointments. No passive monitoring system exists outside hospital; case managers rely on self-reported wellbeing scores that patients stop completing precisely when most at risk.

## The solution
ProdroSense runs silently as a background service on the patient's existing Android or iOS device, requiring zero daily action. Every 6 hours it samples four behavioral streams from standard OS APIs: (1) app session frequency and duration patterns — detecting both the social withdrawal (fewer communication app opens) and the hypomanic surge (erratic long sessions late at night) that typify opposite ends of the prodromal spectrum; (2) GPS location radius — shrinking social geography flags emerging agoraphobia weeks before a hospitalization; (3) Bluetooth-detected device encounters — a passive proxy for real-world social contacts without capturing identity or content; (4) phone charging and screen-on regularity — a non-intrusive circadian anchor whose disruption precedes relapse by 4–8 days in peer-reviewed studies. A personalized transformer establishes each patient's 30-day behavioral baseline and fires a tiered alert to their assigned case manager (not the patient directly) when a multi-day deviation pattern crosses threshold, enabling a brief phone call and medication check before hospitalization becomes necessary. The patient does nothing.

## Why now
Android UsageStatsManager and iOS Screen Time APIs (via MDM consent frameworks, mature post-2022) enable continuous background behavioral fingerprinting without app-level interaction or background location abuse — technically and legally infeasible before 2022. Foundation models for time-series behavioral anomaly detection, fine-tuned on publicly released MONARCA and CrossCheck clinical datasets (2021–2023), mean a personalized model calibrates to a new patient in under 3 weeks rather than requiring months of labeled clinical data collection.

## Who pays and why
German statutory insurers (GKV: AOK, TK, Barmer) pay because 60,000–80,000 schizophrenia hospitalizations annually is a top psychiatric DRG cost driver; DiGA Class IIb listing at €80–120/patient/month delivers provable ROI against even a 15% reduction in hospitalization rate. Community psychiatric social services (SPDi — Sozialpsychiatrische Dienste), funded under §§ 53–60 SGB XII, distribute ProdroSense as a care enhancement tool on per-enrolled-patient fees. Long-acting injectable antipsychotic manufacturers (Janssen, Otsuka, Lundbeck) running real-world outcomes studies of Invega Trinza and Abilify Maintena license de-identified behavioral deviation data as a secondary RWE revenue stream.

## Scores
| Market | Feasibility | Clinical Impact | Regulatory | Author Score |
|:---:|:---:|:---:|:---:|:---:|
| 8 | 8 | 9 | 7 | - |

## Biggest risks
- GDPR sensitivity: Location and behavioral patterns are Article 9 special-category health data; on-device feature extraction with only deviation scores transmitted (never raw behavioral data) is non-negotiable, and German DPA (BfDI) scrutiny of psychiatric monitoring apps is high
- Prodrome non-specificity: Behavioral shifts also occur during life stressors (job loss, bereavement) unrelated to psychosis; false positive rate must be prospectively validated to maintain case manager trust before GKV will list
- Population coverage gap: A minority of schizophrenia patients — particularly older male patients with prominent negative symptoms — are inconsistent smartphone users, limiting reach to the highest-risk subpopulation without a family-carer proxy mode

## Pattern note
Builds on the LiTrace/CogniMS pattern of personalized longitudinal baseline deviation for psychiatric safety monitoring, but shifts from drug-toxicity physiology (motor tremor) or neurological signal (typing dynamics) to a multi-stream passive behavioral fingerprint — the first idea in this series to target prodromal psychosis via behavioral ecology rather than any physiological sensor.
