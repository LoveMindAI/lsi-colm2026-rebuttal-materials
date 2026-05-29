# Mini-Report: Reverse Scoring a Fictional Fact Sheet

This toy demonstration starts with only a fictional name, Megyn Velasquez-Greenblum, and seven ordinary biographical facts. Four independent LLM scorers then infer the same compact psychometric target used for the later profile-writing step.

This is not evidence for the paper's statistical claims. It is a small, inspectable example of the score-to-narrative-to-score logic used in the rebuttal materials.

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

Using the fact-derived composite as the target, we generated four narrative profiles: psychometric-only and psychometric-plus-biographical profiles from Opus 4.6 and Gemma 4 31B. A deterministic scorecard prompt is included as a transparent reference condition.

The narrative profiles reverse-score back toward the synthetic target with high rank-order fidelity in this toy example. Across all dimensions, Opus psychometric-only is highest (`r = 0.951`, MAE `0.502`), followed by Opus interwoven biography (`r = 0.868`, MAE `0.557`), Gemma interwoven biography (`r = 0.814`, MAE `0.711`), and Gemma psychometric-only (`r = 0.810`, MAE `0.627`). The deterministic scorecard is near-perfect by construction (`r = 1.000`, MAE `0.007`).

See `05_profile_reverse_scoring_summary.tsv` for HEXACO and beyond-HEXACO scores shown separately.
