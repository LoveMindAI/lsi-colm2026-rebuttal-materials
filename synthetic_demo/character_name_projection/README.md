# Character Name-Projection Demo

This is a fully fictional bonus demo built after the main synthetic pipeline demo. It starts from names only, asks several models to invent ordinary biographical facts, reverse-scores the resulting fact sheets into compact synthetic psychometric targets, then carries those targets through generated profile portraits and 24-section synthetic LSI transcripts.

The final trio is:

- Cillian Frost
- Haruki Minamoto
- Roxy Saint-Clair

No participant data, production profile-writing prompts, real PARSEL transcripts, or raw model-call logs are included.

## Why This Exists

The main synthetic demo uses one fictional persona, Megyn Velasquez-Greenblum, to make the score-to-profile-to-LSI pathway inspectable. This smaller extension asks a slightly different toy question: if we begin with only a name, do multiple models unfold distinguishable fictional people, and does the later reverse-scoring pipeline preserve those distinctions?

This is not evidence for the paper's statistical claims. It is an inspectable toy stress test of fictional persona construction and trait-shape preservation.

## Model Roles

- Name-only fact generation: Opus 4.6, Gemini 3.1 Pro, and Grok 4.20.
- Fact/profile/LSI scoring panel: Sonnet 4.6, Gemini 3 Flash, and Grok 4.20.
- Profile writers: Opus 4.6 and Gemma 4 31B.
- LSI generator and lexical ablator: Gemini 3 Flash.

## Character Differentiation

The first candidate trio included a more conventional Midwestern repair-and-maintenance character. He was nicely textured, but too close to Cillian in trait space. Roxy Saint-Clair was added as a replacement because she produced a more socially vivid and narratively distinct profile: Louisiana, towing dispatch, real estate, magnolia tattoo, dented sedan, red beans for an uncle, and late-night clarinet.

The final trio is differentiated in text and moderately differentiated in inferred trait space:

| pair | target-shape r | mean absolute target difference |
| --- | ---: | ---: |
| Cillian Frost vs Haruki Minamoto | 0.856 | 0.591 |
| Cillian Frost vs Roxy Saint-Clair | 0.853 | 0.355 |
| Haruki Minamoto vs Roxy Saint-Clair | 0.931 | 0.315 |

The text-level overlap stays low. Across generated 24-section LSIs, cross-character lexical Jaccard overlap averages `0.234`; after lexical ablation it averages `0.207`.

## Recovery Summary

The profile and LSI stages preserve the name+facts target structure reasonably well.

Average 24-section LSI recovery by character:

| character | all-dim r | HEXACO r | beyond-HEXACO r |
| --- | ---: | ---: | ---: |
| Cillian Frost | 0.907 | 0.969 | 0.551 |
| Haruki Minamoto | 0.897 | 0.932 | 0.887 |
| Roxy Saint-Clair | 0.842 | 0.923 | 0.756 |

Average recovery after lexical ablation:

| character | all-dim r | HEXACO r | beyond-HEXACO r | profile-overlap reduction |
| --- | ---: | ---: | ---: | ---: |
| Cillian Frost | 0.926 | 0.974 | 0.605 | 77.4% |
| Haruki Minamoto | 0.904 | 0.930 | 0.939 | 76.3% |
| Roxy Saint-Clair | 0.844 | 0.924 | 0.778 | 78.1% |

All 12 generated LSI transcripts and all 12 ablated transcripts validate at exactly 24 numbered sections.

## File Map

- `01_name_only_facts.md`: model-generated facts plus the consolidated fact sheet for each character.
- `02_synthetic_targets.tsv`: composite target scores inferred from the consolidated facts.
- `02a_fact_scorer_agreement.tsv`: scorer-level agreement for the name+facts target.
- `generated_profiles/`: deterministic scorecards plus generated non-chronological profile portraits.
- `generated_lsi_transcripts/`: 24-section synthetic LSIs from the generated profile portraits.
- `generated_lsi_transcripts_lexical_ablation/`: ablated LSIs with profile-overlap wording reduced.
- `05_profile_reverse_scoring_summary.tsv`, `06_lsi_reverse_scoring_summary.tsv`, `07_lsi_lexical_ablation_summary.tsv`: recovery summaries.
