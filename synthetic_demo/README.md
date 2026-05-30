# Synthetic LSI Pipeline Demo

This folder is a fully synthetic demonstration. Megyn Velasquez-Greenblum is fictional. The demo is intended to make the response pipeline easier to inspect without exposing participant data, production prompt templates, raw profiles, or real transcripts.

The demo begins before profile writing: two models generated ordinary fictional facts for the persona, then four independent scorers inferred a compact psychometric target from the frozen fact sheet. Those scorers agreed strongly on the broad trait shape from sparse facts alone, with mean pairwise `r = 0.871` across the 11 scored dimensions and an average scorer range of `0.46` points on a 1-5 scale.

The synthetic target profile is inferred from the name and seven fictional facts by a four-model scoring panel. We then compare three kinds of conditioning material:

1. a shareable deterministic scorecard prompt
2. generated psychometric-only narrative profiles
3. generated interwoven-biography narrative profiles

The generated profiles and 24-section synthetic LSI transcripts are included as outputs. The shareable reverse-scoring prompt and deterministic scorecard prompt are included. The production profile-writing instructions and generated-profile LSI instructions are not included.

This is a public toy demonstration, not a protocol-equivalent rerun of the paper pipeline. The generated narrative profiles and synthetic LSIs were produced with simplified demo instructions designed for inspectability around a fictional persona. To keep the profile stage from becoming a mini-LSI, the generated-profile prompt used second-person, non-chronological prose and explicitly avoided scenes, interview framing, and life-story language. The outputs should be read as an illustrative score-to-narrative-to-score example, not as disclosure of the study's production prompt templates.

The toy demo also includes a lexical-ablation check for the four generated-profile conditions. The ablation rewrites each generated LSI while avoiding content words from its conditioning profile. Profile-overlap words are reduced by `46.6%` to `76.6%`, while all-dimension recovery remains `r = 0.849-0.922`.

## Bonus Character Demo

`character_name_projection/` contains a small bonus demo with three fully fictional characters: Cillian Frost, Haruki Minamoto, and Roxy Saint-Clair. It starts from names only, asks several models to generate seven ordinary facts for each person, reverse-scores those facts into synthetic psychometric targets, and then carries those targets through generated profile portraits and 24-section LSIs.

This bonus demo is intentionally playful and illustrative rather than claim-bearing. Its useful feature is that the three fictional characters are inspectable as separate people, and the recovery tables show that their inferred target structures remain mostly recoverable after profile generation, LSI generation, and lexical ablation.
