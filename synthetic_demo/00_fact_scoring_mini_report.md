# Mini-Report: Reverse Scoring a Fictional Fact Sheet

This toy demonstration starts with only a fictional name, Megyn Velasquez-Greenblum, and seven ordinary biographical facts. Four independent LLM scorers then infer the same compact psychometric target used for the later profile-writing step.

This is not evidence for the paper's statistical claims. It is a small, inspectable example of the score-to-narrative-to-score logic used in the rebuttal materials.

## What Is Unique Here

The persona is fully synthetic. We first asked two models to invent ordinary biographical facts for a person with a fictional name, consolidated those into seven facts, and then froze that fact sheet before any psychometric profile-writing or LSI generation occurred. No participant data, production profiles, or real transcripts are used anywhere in this demo.

The first interesting result is that the scoring panel found a stable psychometric silhouette from those sparse facts alone. Across the 11 scored dimensions, the four scorers had a mean pairwise correlation of `r = 0.871`; the average scorer range was `0.46` points on a 1-5 scale, with 8 of 11 dimensions varying by no more than `0.5` points and no dimension varying by more than `0.8`. This should not be read as evidence that the fictional person has a "true" personality. It shows that the four independent model raters made similar commonsense trait inferences from the same minimal fictional material, which gives the toy pipeline a coherent synthetic target to carry forward.

## Prompt Scope

This is a public toy demonstration, not a protocol-equivalent rerun of the paper pipeline. The generated narrative profiles and synthetic LSIs were produced with simplified demo instructions designed for inspectability around a fictional persona. To keep the profile stage from becoming a mini-LSI, the generated-profile prompt used second-person, non-chronological prose and explicitly avoided scenes, interview framing, and life-story language. The production profile-writing prompts and generated-profile LSI instructions are not included.

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

Using the frozen composite target, we generated four narrative profiles: psychometric-only and interwoven-biography profiles from Opus 4.6 and Gemma 4 31B. These profiles use second-person, non-chronological portrait prose rather than scenes or life-story structure. We also generated one deterministic scorecard profile that simply exposes the fictional facts and composite scores in a compact, shareable form.

Reverse scoring those profile objects shows that the synthetic target remains recoverable before the LSI stage:

| conditioning object | all-dim r | all-dim MAE | HEXACO r | beyond-HEXACO r |
| --- | ---: | ---: | ---: | ---: |
| deterministic_scorecard | 1.000 | 0.007 | 1.000 | 1.000 |
| opus_4_6_psych_only | 0.940 | 0.491 | 0.919 | 0.964 |
| opus_4_6_interwoven_bio | 0.949 | 0.434 | 0.923 | 0.982 |
| gemma_4_31b_psych_only | 0.849 | 0.705 | 0.956 | 0.950 |
| gemma_4_31b_interwoven_bio | 0.777 | 0.850 | 0.975 | 0.949 |

See `generated_profiles/` for the profile outputs and `05_profile_reverse_scoring_summary.tsv` for the full profile-stage summary.

## LSI Demonstration Check

We then passed the deterministic scorecard and the four generated narrative profiles into a 24-section synthetic LSI generation step. The toy deterministic scorecard instruction is included because it is not part of the production pipeline. The profile-writing instructions and the generated-profile LSI instructions are not included because narrative construction is part of the broader research programme. The generated transcripts themselves are included.

Reverse scoring the generated LSIs tests whether the sparse-fact composite remains recoverable after another transformation into interview-style narrative text.

| conditioning object | all-dim r | all-dim MAE | HEXACO r | beyond-HEXACO r |
| --- | ---: | ---: | ---: | ---: |
| opus_4_6_psych_only | 0.913 | 0.577 | 0.880 | 0.949 |
| opus_4_6_interwoven_bio | 0.848 | 0.625 | 0.869 | 0.996 |
| gemma_4_31b_psych_only | 0.881 | 0.716 | 0.945 | 0.948 |
| gemma_4_31b_interwoven_bio | 0.867 | 0.673 | 0.920 | 0.967 |
| deterministic_scorecard | 0.913 | 0.511 | 0.869 | 0.964 |

See `generated_lsi_transcripts/` for the transcripts and `06_lsi_reverse_scoring_summary.tsv` for the full summary.

## Toy Lexical-Ablation Check

Because the public demo uses simplified instructions, the generated LSI format is visibly more structured than the production pipeline. We therefore added a toy lexical-ablation stress test for the four generated-profile conditions. For each generated psychometric-only or interwoven-biography profile, we extracted profile content-words and rewrote the corresponding LSI transcript while avoiding those words. This tests whether the toy recovery is mostly carried by literal profile wording.

The strict ablation reduced overlapping profile words by `46.6%` to `76.6%`. The synthetic target remained recoverable after ablation: all-dimension recovery stayed between `r = 0.849` and `0.922`, and HEXACO recovery stayed between `r = 0.882` and `0.954`.

| conditioning object | profile-overlap reduction | all-dim r before | all-dim r after | HEXACO r before | HEXACO r after |
| --- | ---: | ---: | ---: | ---: | ---: |
| opus_4_6_psych_only | 46.6% | 0.913 | 0.922 | 0.880 | 0.896 |
| opus_4_6_interwoven_bio | 60.6% | 0.848 | 0.849 | 0.869 | 0.882 |
| gemma_4_31b_psych_only | 76.6% | 0.881 | 0.906 | 0.945 | 0.954 |
| gemma_4_31b_interwoven_bio | 63.6% | 0.867 | 0.907 | 0.920 | 0.882 |

This remains a toy check, not a substitute for the main-paper lexical ablation. Its value is narrower: even in a deliberately inspectable public demo with a more visibly structured LSI format, the recovered trait shape is not erased when profile-overlap wording is substantially reduced.

See `generated_lsi_transcripts_lexical_ablation/` for the ablated transcripts and `07_lsi_lexical_ablation_summary.tsv` for the full summary.
