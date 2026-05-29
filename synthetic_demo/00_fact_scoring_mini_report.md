# Mini-Report: Reverse Scoring a Fictional Fact Sheet

This toy demonstration starts with only a fictional name, Megyn Velasquez-Greenblum, and seven ordinary biographical facts. Four independent LLM scorers then infer the same compact psychometric target used for the later profile-writing step.

This is not evidence for the paper's statistical claims. It is a small, inspectable example of the score-to-narrative-to-score logic used in the rebuttal materials.

## What Is Unique Here

The persona is fully synthetic. We first asked two models to invent ordinary biographical facts for a person with a fictional name, consolidated those into seven facts, and then froze that fact sheet before any psychometric profile-writing or LSI generation occurred. No participant data, production profiles, or real transcripts are used anywhere in this demo.

The first interesting result is that the scoring panel found a stable psychometric silhouette from those sparse facts alone. Across the 11 scored dimensions, the four scorers had a mean pairwise correlation of `r = 0.871`; the average scorer range was `0.46` points on a 1-5 scale, with 8 of 11 dimensions varying by no more than `0.5` points and no dimension varying by more than `0.8`. This should not be read as evidence that the fictional person has a "true" personality. It shows that the four independent model raters made similar commonsense trait inferences from the same minimal fictional material, which gives the toy pipeline a coherent synthetic target to carry forward.

## Prompt Scope

This is a public toy demonstration, not a protocol-equivalent rerun of the paper pipeline. The generated narrative profiles and synthetic LSIs were produced with simplified demo instructions designed for inspectability around a fictional persona. The production profile-writing prompts and generated-profile LSI instructions are not included.

## Scoring Panel

- gemini_3_flash: `google/gemini-3-flash-preview`
- sonnet_4_6: `anthropic/claude-sonnet-4.6`
- qwen_3_6_plus: `qwen/qwen3.6-plus`
- grok_4_20: `x-ai/grok-4.20`

## Composite Shape

The model panel agreed on a recognisable pattern from sparse facts alone: high conscientiousness, high prosocial orientation, high sentimentality, high honesty-humility, above-average agreeableness, moderate openness, average extraversion and emotionality, and lower social anxiety.

The composite target is the per-dimension average across the four scorers. HEXACO dimensions and beyond-HEXACO dimensions are preserved separately in the target table.

See `02a_fact_scorer_agreement.tsv` for the scorer-by-scorer values and ranges.

## Profile-Writing Check

Using the frozen composite target, we generated four narrative profiles: psychometric-only and interwoven-biography profiles from Opus 4.6 and Gemma 4 31B. We also generated one deterministic scorecard profile that simply exposes the fictional facts and composite scores in a compact, shareable form.

Reverse scoring those profile objects shows that the synthetic target remains recoverable before the LSI stage:

| conditioning object | all-dim r | all-dim MAE | HEXACO r | beyond-HEXACO r |
| --- | ---: | ---: | ---: | ---: |
| deterministic_scorecard | 1.000 | 0.007 | 1.000 | 1.000 |
| opus_4_6_psych_only | 0.951 | 0.502 | 0.940 | 0.965 |
| opus_4_6_interwoven_bio | 0.868 | 0.557 | 0.881 | 0.983 |
| gemma_4_31b_psych_only | 0.810 | 0.627 | 0.800 | 0.944 |
| gemma_4_31b_interwoven_bio | 0.814 | 0.711 | 0.900 | 0.943 |

See `generated_profiles/` for the profile outputs and `05_profile_reverse_scoring_summary.tsv` for the full profile-stage summary.

## LSI Demonstration Check

We then passed the deterministic scorecard and the four generated narrative profiles into a 24-section synthetic LSI generation step. The toy deterministic scorecard instruction is included because it is not part of the production pipeline. The profile-writing instructions and the generated-profile LSI instructions are not included because narrative construction is part of the broader research programme. The generated transcripts themselves are included.

Reverse scoring the generated LSIs tests whether the sparse-fact composite remains recoverable after another transformation into interview-style narrative text.

| conditioning object | all-dim r | all-dim MAE | HEXACO r | beyond-HEXACO r |
| --- | ---: | ---: | ---: | ---: |
| opus_4_6_psych_only | 0.928 | 0.541 | 0.908 | 0.965 |
| opus_4_6_interwoven_bio | 0.826 | 0.511 | 0.885 | 0.869 |
| gemma_4_31b_psych_only | 0.909 | 0.625 | 0.920 | 0.973 |
| gemma_4_31b_interwoven_bio | 0.902 | 0.630 | 0.871 | 0.959 |
| deterministic_scorecard | 0.913 | 0.511 | 0.869 | 0.964 |

See `generated_lsi_transcripts/` for the transcripts and `06_lsi_reverse_scoring_summary.tsv` for the full summary.

## Toy Lexical-Ablation Check

Because the public demo uses simplified instructions, the generated LSI format is visibly more structured than the production pipeline. We therefore added a toy lexical-ablation stress test for the four generated-profile conditions. For each generated psychometric-only or interwoven-biography profile, we extracted profile content-words and rewrote the corresponding LSI transcript while avoiding those words. This tests whether the toy recovery is mostly carried by literal profile wording.

The ablation reduced overlapping profile words by `24.6%` to `71.7%`. The synthetic target remained recoverable after ablation: all-dimension recovery stayed between `r = 0.849` and `0.900`, and HEXACO recovery stayed between `r = 0.870` and `0.922`.

| conditioning object | profile-overlap reduction | all-dim r before | all-dim r after | HEXACO r before | HEXACO r after |
| --- | ---: | ---: | ---: | ---: | ---: |
| opus_4_6_psych_only | 24.6% | 0.928 | 0.900 | 0.908 | 0.875 |
| opus_4_6_interwoven_bio | 58.2% | 0.826 | 0.849 | 0.885 | 0.922 |
| gemma_4_31b_psych_only | 58.2% | 0.909 | 0.884 | 0.920 | 0.870 |
| gemma_4_31b_interwoven_bio | 71.7% | 0.902 | 0.893 | 0.871 | 0.896 |

This remains a toy check, not a substitute for the main-paper lexical ablation. Its value is narrower: even in a deliberately inspectable public demo with a more visibly structured LSI format, the recovered trait shape is not erased when profile-overlap wording is substantially reduced.

See `generated_lsi_transcripts_lexical_ablation/` for the ablated transcripts and `07_lsi_lexical_ablation_summary.tsv` for the full summary.
