# Supplemental Notes

These notes give a little more context for points that had to be compressed in the reviewer responses. They are intentionally brief. This repository does not include raw participant psychometrics, participant-level generated narratives, real conversation transcripts, or a full evidence appendix.

## Conversation Correspondence

The response describes the generated-story-to-real-conversation result as modest behavioural triangulation. The relevant scale references are:

- Generated LSI feature to real-conversation same feature: `r = 0.147-0.180`.
- Self-reported HEXACO to coded real-conversation features: mean `|r| = 0.094`.
- Best HEXACO trait selected separately per conversation feature: `r = 0.181`.
- Partner-perceived HEXACO after the PARSEL conversation to self-report HEXACO: mean matched-domain `r = 0.157`.
- Independent LLM recovery of HEXACO from the same short conversations: `r = 0.179-0.221`.

The point is not that the conversation correspondence is large. It is that the short PARSEL conversations contain limited recoverable trait signal, so the observed cross-context correspondence should be read against that constraint.

## Test-Retest Framing

The submitted paper used human test-retest reliability as a familiar reference point. That comparison is useful, but it should not be described as a literal ceiling. A person retaking a questionnaire over time is not the same task as recovering a provided psychometric profile after it has been transformed into generated narrative text.

The cleaner framing is to report human test-retest reliability as a published reliability reference, while separately reporting the direct profile-decode reference for how much signal is available after the Stage 1 profile transformation.

## Stage 1 Profile Transformation

The Stage 1 audit treats the profile step as a measured score-to-narrative transformation. The main checks are:

- generated profiles forbid HEXACO names, explicit scores, percentiles, and instrumental scoring language
- post-generation checks verify that forbidden terms do not appear
- deleting every generated-narrative token that also appeared in the Stage 1 profile changes HEXACO recovery by only `-0.001` to `-0.020`
- deterministic scorecards made directly from source psychometrics recover less than matched narrative profiles

This is why the responses frame the profile step as part of the measured transformation, not as an untested leakage source.

## Human-Reader Pilot

The human pilot was deliberately small and conservative. Native-English Prolific raters saw brief snippets of profile information and generated LSI themes, not full profiles or full narratives. They completed four-option matches at `59.5%` accuracy versus `25%` chance, `t(24)=8.24`, one-tailed `p<1e-8`.

This supports the claim that the generated materials contain person-specific information recoverable by human readers, while staying separate from any claim about expert coding of real transcripts.

## Emotional Reactivity

The emotional-reactivity analysis is scoped to the 24-turn protocol and the valence spine. The compressed response refers to three linked checks:

- Emotionality predicts within-narrative emotional-valence variability after controlling for average valence.
- The strongest facet-level predictor is HEXACO Sentimentality rather than Anxiety or Fearfulness.
- The Sentimentality-to-valence-variability result replicates across independent valence coders, with mean-controlled partial correlations of roughly `r = 0.42-0.50`.

Unconditioned 24-turn narratives also have narrower emotional-valence variability (`0.070-0.088`) than conditioned lanes (`0.102-0.131`), supporting the interpretation that the effect is conditioning-driven rather than default generator behaviour.

## Base Models And Dark-Trait Checks

The base-model checks respond to the concern that instruction tuning or safety tuning might shape the result, especially for dark-trait-adjacent material. Full-N base-model generations exceeded participant-label-shuffle controls, so recovery is not limited to chat-model compliance. On the 50-PID dark/bright slice, however, base models did not show a special advantage over the regular profile generators.

To match the base-model setup in *Deep Binding of Language Model Virtual Personas: a Study on Approximating Political Partisan Misperceptions* (Kang et al., arXiv:2504.11673), we also ran `mistralai/Mistral-Small-24B-Base-2501` on the dark/bright slice. It recovered HEXACO at `r = 0.556`, dark-axis aggregate at `r = 0.607`, and PPTS total at `r = 0.657`. These are meaningful signals, but they do not support switching the pipeline to base models for the camera-ready version.

## Matched Human Life Stories

The cleanest comparison would be matched human-authored life stories from the same participants or from a dataset with comparable psychometrics. We did seek access to two such datasets during the initial experimental phase, but did not secure matched access in time. That remains the central follow-up rather than an analysis available in the present PARSEL data.
