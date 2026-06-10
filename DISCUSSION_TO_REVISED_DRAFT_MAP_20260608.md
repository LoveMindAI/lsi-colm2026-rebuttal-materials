# LSI Review Discussion to Revised Draft Map

Date: 2026-06-08  
Associated paper: COLM 2026 Submission #692, *Stories of Your Life as Others: A Round-Trip Evaluation of LLM-Generated Life Stories Conditioned on Rich Psychometric Profiles*  
Associated draft in this materials packet: `camera_ready_draft_20260608/lsi_colm2026_10page_camera_ready_draft_20260608.pdf`

## Purpose

This document maps the review-discussion concerns to the revised discussion-stage draft. It is intended to make the revision trace inspectable for Area Chairs and reviewers without requiring readers to reconstruct the full OpenReview exchange.

The revised draft narrows the paper's scientific object: it is not a claim that generated life-story interviews are substitutes for matched human-authored LSIs, nor a claim that the paper identifies the training-data source or mechanism of the capability. The scoped claim is that measured psychometric profiles can be transformed into controlled profile prose and generated LSI-style narrative such that source individual-difference structure remains recoverable across participants, generators, scorers, controls, and reference analyses.

## June 9 Polish Patch

After an additional audit of the revised draft, we made a small clarification pass to remove several possible ambiguities before Area Chair review:

1. **Scorecard reference provenance clarified.** The Table 2 row previously labelled "Matched PsychNarr reference" is now labelled "Matched 4-part PsychNarr subset." This number comes from the strict scorecard-control subset using the same two 4-part generators and two scorers as the scorecard controls, not from the broader 20-row primary matrix in Table 1.
2. **Qwen family ambiguity resolved.** The base/post-trained Qwen comparison now states that Qwen3.5-35B-A3B is a different, larger sibling pair than the Qwen 3.6 27B checkpoint used as one of the four main LSI generators.
3. **Conversation-reference figure split.** Figure 3 now uses two panels: short participant-conversation references on the left and generated-LSI round-trip recovery on the right. The caption explicitly states that these are different constructs.
4. **Uncertainty wording tightened.** Figure 1 no longer calls generator-scorer row intervals participant-level confidence intervals; the caption now describes them as descriptive intervals over generator-scorer rows.
5. **Emotional-reactivity covariate named.** Appendix F now states that independent-coder partial correlations control for mean valence.
6. **Rebuttal-process scaffolding reduced.** Appendix wording was neutralised so the manuscript reads as a revised paper rather than a discussion-history log.
7. **Final construct and limitation wording tightened.** The main text now uses "narrative-mediated psychometric binding" as the primary construct name, and the limitations state that the main narrative rows hold the profile writer constant while deterministic scorecard controls bypass the profile writer and still recover signal.

## High-Level Changes

1. **Claim narrowed.** The draft now frames the result as psychometric-linguistic encoding and decoding through generated narrative, not unrestricted personality simulation or human-LSI equivalence.
2. **Research questions rebuilt.** The paper is organised around four explicit questions: round-trip recovery, controls, base/pretrained generators, and bounded human-language references.
3. **Profile transformation made explicit.** The first transformation from measured scores to controlled profile prose is analysed directly instead of treated as hidden prompt craft.
4. **Main recovery matrix refreshed.** The draft reports the full $N=290$ matrix across four main generators, two profile formats, two LSI lengths, and five independent scorers.
5. **Direct handoff and facts controls added.** Scorecard and facts-only controls test whether recovery comes from exact numeric handoff or biographical anchors.
6. **Shared-method concerns stress-tested.** The revised draft adds cross-family generator/scorer checks, transparent lexical schema tests, severe sentence-deletion ablations, and a human-reader calibration.
7. **Base/pretrained model wing added.** Four true base/pretrained model families are compared with matched post-trained or instruct counterparts where available.
8. **Conversation evidence reframed.** PARSEL conversations are used only as low-bandwidth participant-language references, with denominators that make their modest signal interpretable.
9. **Schema and provenance separated.** The draft treats fine-grained schema as a plausible mechanism while making clear that acquisition provenance remains future work.
10. **Appendix expanded.** The appendix now routes readers to condition terminology, profile-writer bake-off, model sweeps, scoring/coding, emotional reactivity, base models, schema tests, corpus inspection, and evidence manifests.

## Draft Location Map

| Concern area | Revised draft location | What changed |
|---|---|---|
| Scope and central claim | Abstract; Introduction; Discussion; Limitations; Conclusion | The paper now states that the assay measures profile-to-language preservation, not whether synthetic LSIs replace human life-story interviews. |
| Scientific framing | Introduction; Related Work; RQs | The draft frames the result as narrative-mediated psychometric binding in an operational sense: measured individual differences remain attached to generated language across transformations. |
| Stage 1/profile construction | Method: Profile construction; Results RQ1; Appendix B | The profile step is now described and audited as a measured score-to-profile transformation, with direct profile-decode references and a profile-writer bake-off. |
| Main recovery evidence | Results RQ1; Table 1; Figure 1 | The headline recovery matrix is reported across four generators, two profile formats, two LSI lengths, and five scorers. |
| Direct handoff and facts controls | Results RQ2; Table 2; Appendix C | Scorecards and facts-only controls are reported as alternatives to narrative profile conditioning. |
| Provider/family dependence | Method; Results RQ1/RQ2; Appendix C | The draft reports scorer variation and same-family versus cross-family generator/scorer comparisons. |
| Transparent schema and lexical leakage | Results RQ2; Discussion; Appendix G; Figure 4 in appendix | The draft reports transparent lexicons, residualisation, and sentence deletion that removes every transparent-schema-hit sentence before rescoring. |
| Base/pretrained models | Results RQ3; Figure 2; Appendix F | The draft adds full-$N$ base/pretrained generators and matched post-trained/instruct comparisons. |
| Human-reader calibration | Results RQ4; Appendix D | A non-LLM reader matching task is reported as a calibration that generated materials carry person-profile signal. |
| PARSEL conversations and Figure 3 issue | Results RQ4; Figure 3; Discussion; Appendix D | The old metric-mixing comparison is replaced by a low-bandwidth conversation-reference figure and denominator discussion. |
| Emotional reactivity | Results RQ4; Appendix E | The emotional-valence variability check is retained as secondary content-level evidence, with unconditioned baselines and independent coders in the appendix. |
| Provenance and mechanism | Related Work; Discussion; Limitations; Appendix H | The draft distinguishes behavioural evidence, corpus inspection, and future mechanistic acquisition work. |
| Ethics and privacy | Ethics Statement; Limitations | The draft clarifies that profile-conditioned generated text can carry recoverable psychometric signal and therefore raises privacy considerations. |

## Reviewer Concern Map

### Scope: Personality Simulation vs. Psychometric Signal Preservation

**Concern.** Several comments raised the possibility that the submitted framing sounded like a claim of robust personality simulation or faithful human-like expression.

**Response in the revised draft.**

- The Abstract now asks whether measured psychometric profiles survive transformation into open-ended narrative.
- The Introduction defines the contribution as a behavioural assay for psychometric-linguistic encoding and decoding.
- The Discussion states that the central finding is narrative-mediated psychometric binding in a strictly operational sense.
- The Limitations state that the study does not establish that synthetic LSIs faithfully reproduce how the same people would write or speak in matched human LSIs, and does not establish unrestricted person simulation.
- The Conclusion repeats the bounded claim: generated narrative preserves profile structure, but the assay does not establish ecological equivalence to human autobiographical writing.

**Scope limit.** Matched human-authored LSIs remain the next validation study. The present paper evaluates profile-to-generated-language preservation.

### Matched Human LSIs and PARSEL Conversation Evidence

**Concern.** Reviewers asked whether generated LSIs match how real people would express personality, and noted that PARSEL conversations are short, noisy, and format-mismatched.

**Response in the revised draft.**

- The Method explains that PARSEL conversations are the only participant-authored language tied to the same psychometric profiles, and that they are used as human-language context rather than format-matched validation.
- Results RQ4 reports the conversation denominators:
  - Participants' own HEXACO scores predict coded conversation features at mean $|r|=.094$.
  - A featurewise best-trait reference reaches $.181$.
  - Partner-perceived HEXACO correlates with self-report at mean $r=.157$.
  - Independent LLM scoring of short conversations recovers HEXACO at $r=.179$--$.221$.
  - Generated-story-to-conversation same-feature correspondence is $r=.147$--$.180$.
- Figure 3 now visualises these references as a low-bandwidth comparison rather than as evidence of matched human-LSI equivalence.
- The Discussion compares PARSEL's short conversations to richer human open-text settings such as stream-of-thought writing and multi-day diaries, and explains why the bridge remains modest.

**Scope limit.** The revised draft treats the conversation analysis as modest behavioural triangulation, not validation that synthetic LSIs match human LSIs.

### Metric-Mixing Figure and Conversation Gap

**Concern.** One reviewer pointed out that the submitted Figure 3 mixed metrics and did not adequately discuss the gap between LLM scoring of real conversations and round-trip LSI recovery.

**Response in the revised draft.**

- The old metric-mixing figure has been removed.
- The revised Results use Pearson references for the short-conversation comparisons.
- The new Figure 3 frames short conversations as a low-bandwidth participant-language reference and directly shows that generated-LSI round-trip recovery is much higher because it uses the full generated narrative.

**Scope limit.** The draft does not use short conversations as the central evidence for the paper's main claim.

### Stage 1 Profile Writing and Leakage

**Concern.** Reviewers worried that the profile-writing step could inject trait descriptions or behavioural examples that scorers simply read back.

**Response in the revised draft.**

- The Method now treats profile construction as the first measured transformation, not hidden preprocessing.
- The draft defines two main public profile formats:
  - *Psychometric Narrative Profile* / *PsychNarr*: controlled profile prose from measured psychometrics, without personal facts or explicit score language.
  - *Psychometric Narrative + Facts* / *PsychNarr+Facts*: the same psychometric narrative profile with non-diagnostic biographical anchors.
- Results RQ1 reports direct profile-decode references before LSI generation: HEXACO/Beyond10/Continuous16 values of $.915/.780/.834$ for *PsychNarr* and $.911/.780/.833$ for *PsychNarr+Facts*.
- Appendix B reports the full profile-writer bake-off and the rationale for selecting Gemma 4 31B IT as the default writer.
- Results RQ2 adds direct scorecard controls and facts-only controls.

**Scope limit.** High direct profile-decodability shows that the profile transformation preserves psychometric information; it is not presented as evidence of human-like simulation.

### Direct Numeric Handoff and Facts-Only Alternatives

**Concern.** Reviewers asked whether the pipeline merely hands psychometric scores through the system, or whether biographical anchors carry the signal.

**Response in the revised draft.**

- Table 2 reports compact exact-score and glossary scorecard controls. They recover meaningful signal, but less than the matched narrative profile condition.
- Table 2 also reports facts-only controls: Gemini-generated facts-only inputs recover HEXACO at $.102$, and Gemma-generated facts-only inputs at $.149$.
- The Discussion interprets the narrative transformation as a richer intermediate representation than a score table: it can express covariance, tension, and interaction among traits.

**Scope limit.** The draft does not claim that numeric scorecards contain no signal. It claims they do not match the full narrative profile condition.

### Shared-Method Variance and LLM-Dense Pipeline

**Concern.** Reviewers noted that the submitted pipeline used LLMs as profile writers, generators, scorers, coders, matchers, and auditors.

**Response in the revised draft.**

- The Method and Limitations explicitly name the pipeline as LLM-dense.
- Cross-family generator/scorer checks show same-family rows do not outperform cross-family rows on HEXACO/Beyond10 recovery.
- Deterministic scorecard controls remove the LLM profile writer.
- Facts-only controls test biographical grounding.
- Transparent lexical schemas recover signal without an LLM judge.
- Severe sentence-drop ablations remove transparent trait-language sentences before rescoring.
- The human-reader calibration tests whether non-LLM readers can recover person-profile signal from generated snippets.

**Scope limit.** The revised draft says these controls reduce shared-method concerns but do not eliminate them.

### Model-Family Bias, Prompt Writer Choice, and Matrix Breadth

**Concern.** Reviewers asked whether the result depended on a particular proprietary writer, scorer, or model family.

**Response in the revised draft.**

- The main recovery matrix crosses four LSI generators, two profile formats, two LSI lengths, and five independent scorers, all at $N=290$.
- Results RQ1 reports scorer-level Continuous16 means across five scorers.
- Results RQ2 reports that same-family generator/scorer cells do not outperform cross-family cells.
- Appendix B reports the full profile-writer bake-off across frontier and open-weight writers.
- Appendix C reports additional generator sweeps, including smaller/open-weight lanes, less-filtered variants, and a diffusion-language model.

**Scope limit.** The draft does not claim all models behave identically. It reports robust recovery across a deliberately broadened model ecology.

### Base/Pretrained Models and Instruction-Tuned Compliance

**Concern.** Reviewers worried that instruction-tuned models might be especially good at following explicit trait-portrayal schemas, inflating recovery without demonstrating a deeper profile-to-language capability.

**Response in the revised draft.**

- RQ3 is now devoted to base/pretrained generators and post-training.
- Figure 2 and Appendix F report full-$N$ true base/pretrained generators:
  - Mistral Small 24B: $.453$--$.461$ HEXACO recovery.
  - Gemma 4 31B: $.467$--$.522$.
  - Qwen3.5-35B-A3B: $.645$--$.672$.
  - OLMo 3 32B: $.494$--$.529$.
- Matched post-trained/instruct counterparts are higher in all four families under available scorer coverage.
- The Discussion frames this as evidence that the capability is not created by instruction-tuned chat compliance, while post-training improves task fit and controllability.

**Scope limit.** Base-model recovery does not prove human-LSI equivalence or identify the mechanism. It narrows the behavioural alternative that recovery is merely an instruction-following artefact.

### Fine-Grained Schema Hypothesis

**Concern.** A reviewer argued that a fine-grained schema learned from psychometric literature could predict the same facet-specific, mean-independent patterns.

**Response in the revised draft.**

- The Discussion treats a fine-grained psychometric schema as a plausible mechanism rather than a straw alternative.
- Results RQ2 and Appendix G make transparent schema operational:
  - A lexical schema built from public trait/facet descriptors recovers mean HEXACO6 signal of $.511$ without an LLM judge.
  - After residualising LLM recovery on all six HEXACO lexicons, mean HEXACO6 recovery remains $.668$.
  - After residualising on every schema lexicon plus length, it remains $.641$, with all $192/192$ tests significant.
  - Severe sentence deletion removes every generated sentence containing any transparent-schema lexical hit; recovery remains substantial.
- Appendix H reports corpus-inspection checks over OLMo-family indexes and generated-output n-grams.

**Scope limit.** The draft does not rule out a rich latent schema. It rules out the obvious lexical/shallow-template version as a complete explanation and treats richer schemas as future mechanism work.

### Emotional Reactivity and Content-Level Structure

**Concern.** Reviewers asked whether emotional-reactivity findings reflected a coarse "emotional people write more emotional prose" schema or default generator behaviour.

**Response in the revised draft.**

- Results RQ4 reports emotional reactivity as a secondary content-level check.
- Appendix E reports that profile-conditioned LSIs have broader emotional-valence variability than unconditioned baselines.
- Appendix E reports unconditioned SD ranges of $.070$--$.088$ versus conditioned ranges of $.102$--$.131$.
- Appendix E reports independent valence-coder replication of the Sentimentality-to-valence-variability effect, with mean partial correlations of $.449$, $.450$, and $.424$ across additional coders.

**Scope limit.** The draft frames emotional reactivity as generated-LSI structure, not proof of matched human expressive fidelity.

### Human-Reader Calibration

**Concern.** Reviewers asked for evidence beyond LLM scoring or annotation.

**Response in the revised draft.**

- Results RQ4 and Appendix D report a Prolific reader calibration.
- Twenty-five native-English raters completed 625 four-option matches between short person-description snippets and generated LSI theme snippets.
- Readers selected the correct match on 372/625 trials, for 59.5% accuracy against 25% chance.
- The task is described as limited-information and conservative.

**Scope limit.** This is not expert coding of original PARSEL transcripts or matched human LSIs. It is a non-LLM calibration that generated materials carry person-profile signal.

### Benchmark Framing and Test-Retest Language

**Concern.** Reviewers cautioned against treating generated-profile recovery as directly comparable to personality-from-human-text benchmarks or human test-retest reliability.

**Response in the revised draft.**

- Related Work now treats prior personality-from-text studies as recognition-side context rather than direct competitors.
- The Discussion compares PARSEL's short conversations to richer human-text settings only to calibrate bandwidth.
- The revised Abstract and main Results no longer present human test-retest reliability as a literal ceiling.
- Direct profile-decode references are reported separately from generated-LSI recovery.

**Scope limit.** The paper does not claim to beat human personality inference benchmarks on the same task. It reports a different transformation-and-recovery assay.

### Missing Citation, Scale Polarity, and Psychometric Target Clarity

**Concern.** One reviewer noted a missing PPTS citation and requested clearer target/polarity handling.

**Response in the revised draft.**

- The Method cites the Psychopathic Personality Traits Scale source.
- The target set is explicitly defined as HEXACO6, Beyond10, and Continuous16.
- Trust, PPTS, SIAS, and SVO are listed as the non-HEXACO targets.

**Scope limit.** The revised draft reports aggregate recovery over target groups; more granular target-level tables remain appendix/supporting-material territory.

### Corpus Inspection and Provenance

**Concern.** Reviewers asked whether the observed mapping reflects faithful individual-difference encoding or learned trait-portrayal templates, raising questions about acquisition source.

**Response in the revised draft.**

- Related Work and Limitations separate behavioural capability from corpus exposure and mechanism.
- Appendix H reports OLMo-family corpus inspection:
  - Generated 5-gram and 10-gram exact-count checks.
  - Exact phrase probes for psychometric and narrative bridge phrases.
  - OLMoTrace-style checks of deleted schema-hit sentences.
- The Discussion says base/pretrained controls and OLMo-family corpus probes narrow and stress-test interpretation while leaving mechanistic acquisition as future work.

**Scope limit.** The draft explicitly states that corpus inspection is not provenance proof and does not identify circuits, features, attention heads, or the exact training-data source.

### Language, Sampling, Privacy, and Generalisation

**Concern.** The review discussion pushed the revised draft toward clearer limits around generalisation and deployment.

**Response in the revised draft.**

- Limitations now state that the evidence is English-only and drawn from PARSEL's WEIRD participant context.
- The draft identifies translation, multilingual profile construction/scoring, and lower-resource linguistic contexts as future work.
- The Ethics Statement notes that recoverable personality information from generated text raises privacy considerations.

**Scope limit.** The revised draft does not claim cross-cultural, multilingual, or deployment-ready validity.

## Supporting Materials Map

| File | Main purpose | Draft claim it supports |
|---|---|---|
| `camera_ready_draft_20260608/lsi_colm2026_10page_camera_ready_draft_20260608.pdf` | Revised discussion-stage draft | Main revised manuscript and appendix. |
| `reviewer_responses/reviewer_B2W7.md` | Initial response to B2W7 | Shared-method variance, human calibration, conversation denominators, model-family checks, emotional-reactivity controls. |
| `reviewer_responses/reviewer_hoWs.md` | Initial response to hoWs | Claim narrowing, real-conversation reframing, Stage 1 audit, leakage checks, base models, human check. |
| `reviewer_responses/reviewer_ZufX.md` | Initial response to ZufX | PARSEL limits, metric matching, conversation denominators, trait-schema concern, format mismatch. |
| `supplemental_notes/SUPPLEMENTAL_NOTES.md` | Compact notes for compressed rebuttal claims | Conversation references, test-retest framing, Stage 1 transformation, human-reader pilot, emotional reactivity, base models, matched-human-LSI limitation. |
| `synthetic_demo/README.md` | Fictional mini-demo without participant data | Inspectable toy example of sparse-fact scoring, profile reverse scoring, LSI reverse scoring, and lexical ablation. |

## Claims Deliberately Not Made

- The paper does not claim synthetic LSIs faithfully reproduce matched human-authored LSIs.
- The paper does not claim unrestricted or accurate simulation of a specific person.
- The paper does not claim that models are "becoming" participants or instantiating human autobiographical cognition.
- The paper does not claim that the PARSEL conversation bridge validates human-LSI equivalence.
- The paper does not claim to identify the training-data source or mechanistic origin of the mapping.
- The paper does not claim that transparent lexical schemas are irrelevant; it claims they are incomplete as a full explanation.
- The paper does not treat human test-retest reliability as a literal ceiling for profile-to-generated-text recovery.
- The paper does not claim cross-linguistic or non-WEIRD generalisation.

## What Remains Future Work

1. **Matched human LSIs.** A dataset with psychometrics plus human-authored LSIs or long-form self-narration from the same participants would test format validity directly.
2. **Mechanistic acquisition.** Base-model controls and corpus inspection narrow behavioural alternatives, but exact acquisition provenance requires future mechanistic and corpus work.
3. **Multilingual and cross-cultural validation.** The current study is English-only and PARSEL-based.
4. **Richer human annotation.** The human-reader task calibrates generated snippets; it does not replace expert coding of human transcripts or matched human narratives.

## One-Sentence Trace

The review discussion pushed the paper from a broad personality-simulation framing into a narrower and stronger behavioural assay: measured psychometric profiles are transformed into controlled prose and generated life-story narrative, substantial source structure survives that transformation, and the revised draft now documents the controls, limits, and future validation steps needed to interpret that finding responsibly.
