# Pre-registration — LLM writing style in public petitions (pipeline v6.0)
Generated: 2026-07-28T21:27:26
Contact: navians@post.bgu.ac.il

## Design
Observational event study around the public release of ChatGPT (2022-11-30), with secondary
dose dates GPT-4 (2023-03-14) and free GPT-4o (2024-05-13). Unit = petition document.
Headline sample: platforms with a WITHIN-PLATFORM pre/post contrast and anchor_type='source'
(uk_2019; canada; plus any source passing the ≥150-docs-per-era rule in cell 11.13).

## Confirmatory hypotheses (all others exploratory)
H1 (event study): In uk_2019, quarterly event-study coefficients on lex_score_v6 (cell 11.6)
   are ≈0 pre-2022Q4 (max |pre-trend coef| < 0.10 SD) and rise after 2022Q4; permutation test
   over placebo cut-dates gives p_perm < .05.
H2 (specificity): In the fixed-effects ITS (cell 11.7), post_chatgpt > 0 on lex_score_v6 while
   the IDENTICAL model on placebo_z_v6 meets the PASS rule (placebo n.s. AND |placebo| < 50%
   of the real coefficient).
H3 (prevalence): The split-half excess-vocabulary lower bound π_lb (cell 11.8) is > 0 with a
   95% bootstrap CI excluding 0 for 2024Q1+ in uk_2019 or uk_current, and in canada.
H4 (replication): The direction of the lex effect replicates (d > 0) in ≥1 non-UK,
   source-anchored platform (cell 11.13) with the placebo d CI covering 0.

## Frozen analysis decisions
- Scores: v6 source-anchored z-scores on NFKC/quote/dash-normalized text; MTLD not TTR.
- Weights: w_v6 = dup_weight × topic_weight × len_weight (cells 11.3–11.4); never optional.
- SEs: cluster by week (ITS/event study); HC1 elsewhere; BH-FDR across markers (11.9).
- Exclusions: senedd_archive and any anchor_type≠'source' rows are sensitivity-only.
- Prevalence: candidate-word floor, DELTA_MIN=0.004, RATIO_MIN=1.8, FIT_QS=8, split-half
  selection/estimation, banned = placebo ∪ NMF-topic words ∪ TOPIC_STOP, as coded in 11.8.
- Signatures: quasi-Poisson with log(days_open) offset (11.11); pre-era model is the benchmark.
- Moderation: harmonized buckets per 11.12; unmapped codes reported, never silently dropped.
- Secular-growth guard: any signature effect must replicate on the within-source×quarter
  percentile outcome and the source×quarter-FE quasi-Poisson (11.11b); if 11.11 and 11.11b
  disagree, 11.11b is the reported specification.
- Like-for-like rule: pre/post effects are computed within a platform only; pooled statements
  never mix platform types (government vs commercial vs NGO — coverage matrix in 11.11b).
- STAGED INTEGRATION of the Change.org OSF release: stage A analyses government platforms
  alone; stage B analyses changeorg sources alone against their own pre-era; stage C (pooled,
  source FE) is reported only after A and B, and platform-type-stratified rows come first.
- Change.org exposure: signature counts are a 2025-01-09 scrape snapshot (paper Methods);
  exposure offsets use creation-to-snapshot days; deletion-survivorship is declared (the
  release contains only petitions not deleted by the snapshot).

## Declared limitations (stated in the paper regardless of results)
Marker-based shifts are UPPER bounds on direct LLM use (secular human drift); π_lb is a LOWER
bound; Korean detection is weakly benchmarked (absent from MULTITuDE); who-writes vs how-they-
write cannot be separated without author identifiers on government platforms.

## Exploratory (reported as such)
Homogenisation panels (11.10), threshold/Cox models (11.11), duplicate-rejection channel
(11.12), per-marker ranking beyond the professionalisation split (11.9), all non-anchored
sources, senedd_archive sensitivity runs, Binoculars TPR (11.14), within-writer userID
analyses (11.17), title↔text alignment (11.18), embedding-geometry probes (11.19), and the
pre-era LM surprise curve (11.20).
