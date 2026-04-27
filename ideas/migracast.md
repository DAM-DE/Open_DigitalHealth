# MigraCast
> Predict migraine prodrome 12–24h early via passive smartwatch + phone signals → optimal abortive timing for 12M German migraineurs

## The problem
Migraine affects 12 million people in Germany and 70 million in Europe, generating €27B in annual productivity losses and representing the leading cause of disability-adjusted life years among women under 50. The core failure mode is timing: 75% of migraineurs take abortive medications (triptans, gepants) reactively — only once pain begins — by which time the triptan window is closing and the attack is established. Current tools are symptom diaries (active logging) or trigger trackers, all reactive; no passive system exists to identify the premonitory phase — the 12–48 hour hypothalamic window before headache onset — in real time.

## The solution
MigraCast runs silently on the user's iPhone + Apple Watch. Every night, it aggregates five passive streams the device already captures: HRV deviation from personal baseline, sleep fragmentation, barometric pressure rate-of-change (iPhone barometer), ambient light exposure inferred from screen-brightness auto-adjustments, and walking cadence variability. A personalised transformer model — tuned to each user after their first 3–4 attacks — learns their individual prodromal fingerprint and, when the composite pattern crosses threshold, fires a single push notification: "Your patterns match your pre-migraine window. If you have an abortive prescribed, this may be the right time — confirm with your plan." The user does nothing daily; the alert arrives only when relevant.

## The Evidence
The premonitory phase of migraine is documented in >200 peer-reviewed studies; autonomic changes (HRV, temperature) and barometric sensitivity predict onset 12–72h early with 60–80% sensitivity in prospective diary studies (Giffin et al., Neurology 2003; Laurell et al., Cephalalgia 2016). RCTs show triptans taken in the premonitory phase achieve 60–70% pain-free rates at 2 hours versus 30–40% when taken during established headache (Manack et al., Headache 2011). Passive multi-signal modeling has not been commercialized because personal baseline training required infrastructure that, until on-device ML arrived, was too expensive and latency-prone for real-time use.

## Why now
Apple Watch Series 9 + iPhone 15 expose HRV, sleep staging, continuous barometric pressure, and ambient-light inference via HealthKit — all APIs are live and accessible to third-party apps as of 2023. On-device transformer inference (Core ML, 8MB model) runs the prodrome classifier at <2% battery overhead; this was not achievable before the A16/A17 Neural Engine. The gepant class of abortives (rimegepant, atogepant) — unlike older triptans — are approved for both preventive and acute use, making precise timing recommendations legally and clinically clear.

## Who pays and why
German statutory health insurers (GKV) reimburse DiGA Class IIa apps at €35–70/patient/month — MigraCast targets a DiGA listing supported by a 200-patient prospective study showing reduced attack frequency as the primary endpoint. Allergan/AbbVie (Ubrelvy), Pfizer (Nurtec), and AstraZeneca need real-world abortive timing data for gepant outcomes-based contracts; MigraCast sells them an anonymised RWE feed showing medication use in true prodrome vs. headache phase. DTC subscription at €12–18/month captures the 2M German chronic migraineurs who pay out-of-pocket for anything that reduces attack burden.

## Scores
| Market | Feasibility | Clinical Impact | Regulatory | Author Score |
|:---:|:---:|:---:|:---:|:---:|
| 8 | 9 | 8 | 9 | - |

## Biggest risks
- Personal model cold-start: the classifier requires 3–4 labeled attack events to personalise, meaning new users face 4–8 weeks of no prediction benefit — high early churn risk
- Barometric pressure + HRV generates false positives on workout days, hot weather, and altitude travel; robust noise-rejection is required to maintain clinical trust
- Gepant/triptan timing advice sits in a regulatory grey zone — alerts must be framed as behavioral nudges (not dosing instructions) to stay in DiGA Class I/IIa and avoid BfArM scrutiny

## Pattern note
Extends the FlareCast/ExaWave passive multi-signal personal baseline pattern to migraine — a condition where the intervention window (prodrome) is clinically proven but systematically missed, and where the payoff per alert (attack averted) is immediate and subjectively obvious to the user, accelerating retention and trial evidence.
