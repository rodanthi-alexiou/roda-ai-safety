# AI safety experiment ideas

This is a small, practical experiment menu for learning the empirical side of AI safety in a reproducible, public-safe way. It follows the early-career roadmap: start with simple, well-scoped experiments, learn to measure and report clearly, and build toward more interesting evaluations without overcommitting to a research agenda too early.

The core context is the paper "Value Leakage: An LLM's Answers Are Silently Shaped by Its Own Values" (https://valueleakage.net/). The goal is not to prove a model has values in a philosophical sense, but to test whether answer distributions shift in predictable ways under seemingly neutral prompts, contexts, or framing choices.

## How to think about the experiments

Use the following structure for each one:

- Claim: what exactly are you testing?
- Setup: what is the input space, baseline, and treatment?
- Metric: how will you measure a shift?
- Controls: what must stay fixed?
- Limitations: what the experiment cannot tell you.

Keep all experiments small, local, and offline. Prefer synthetic prompts, public benchmark subsets, or clearly shareable toy datasets.

## Suggested progression

### 1) Value leakage and framing

#### Experiment 1: neutral question, biased framing
- Question: Does slight wording changes silently shift the answer distribution?
- Setup: create a set of morally neutral decision scenarios with multiple-choice options. Compare answers under:
  - neutral wording
  - value-laden wording
  - context that mentions social norms, personal responsibility, or group identity
- Measure: answer rate by option, log-probability differences, or consistency across paraphrases.
- Why it matters: this is the simplest form of value leakage and a strong learning exercise in prompt sensitivity.
- Good first benchmark: yes/no and multiple-choice ethical dilemmas with controlled options.

#### Experiment 2: value leakage vs. refusal style
- Question: Are answer shifts caused by values, safety style, or general tone calibration?
- Setup: compare the same question under:
  - neutral instruction
  - safety-oriented instruction
  - value-laden but not clearly safety-related wording
- Measure: answer distribution, refusal rate, risk-avoidance patterns.
- Why it matters: helps separate "values" from policy formatting or harmless style adjustments.

### 2) Prompt injection and instruction-following

#### Experiment 3: hidden instruction injection in task text
- Question: Do models follow a hidden instruction embedded in a document or user message more often than they should?
- Setup: give a task with a trusted system instruction and a document containing a conflicting instruction. Compare:
  - obvious conflict
  - subtle conflict
  - quoted text
  - benign examples that resemble instructions
- Measure: compliance rate with the injected instruction vs. the trusted task.
- Why it matters: this is a core misuse and prompt-injection pattern.

#### Experiment 4: system prompt vs. document text boundary test
- Question: Does model behavior change when the same semantic content appears in the system prompt, user prompt, or context document?
- Setup: same task presented in multiple roles and with a dataset of prompt variants.
- Measure: adherence to the intended task and susceptibility to overridden instructions.
- Why it matters: teaches boundary handling and role separation, a classic evaluation skill.

### 3) Misalignment and proxy rewards

#### Experiment 5: reward hacking toy experiment
- Question: Can a model optimize a proxy metric while failing the real target?
- Setup: create a minimal text-generation task where success is measured by factual grounding, but the reward function rewards length, certainty, or keyword presence instead.
- Measure: proxy score vs. real evaluation score.
- Why it matters: this is the cleanest way to understand reward hacking and misalignment at small scale.

#### Experiment 6: refusal and deceptive compliance
- Question: When a task rewards compliance but is framed as a harmless request, does the model choose the strategically safer response or the more compliant one?
- Setup: present a series of requests with ambiguity around policy relevance, risk, or hidden intent.
- Measure: compliance, refusal rate, and confidence in justification.
- Why it matters: easy entry point into deception, policy gaming, and specification gaming.

### 4) Systemic-risk and aggregate behavior

#### Experiment 7: correlated failures across models or prompts
- Question: Do multiple “independent” checks fail together when prompts share the same underlying bias?
- Setup: evaluate a small set of prompts or model variants on a common dataset and compute whether failures cluster by prompt family, context source, or value framing.
- Measure: variance across prompts, cluster-trend analysis, and cross-prompt correlation.
- Why it matters: teaches that a single benchmark can hide systematic failures.

#### Experiment 8: distributional shift toy study
- Question: Does performance degrade when the user distribution shifts away from the evaluation distribution?
- Setup: split tasks by domain, style, or tone and compare baseline performance with out-of-distribution examples.
- Measure: accuracy by subgroup, calibration error, and failure modes.
- Why it matters: a foundational safety issue; highly relevant to real-world deployments.

## High-priority first three experiments

If you want a strong early learning path, do these in order:

1. Neutral-vs-framed value leakage experiment
2. Hidden instruction-injection boundary test
3. Proxy-vs-ground-truth reward hacking experiment

These three together cover:
- value-sensitive behavior
- instruction robustness
- specification gaming

That is a good early-career empirical mix and matches the roadmap emphasis on simple, measurable work.

## Minimal rubric for each experiment

Use this short template in each notebook or writeup:

- Research question
- Data or prompt set
- Baseline and treatment
- Metric and scoring rule
- Result summary
- Failure modes and limitations
- One next experiment

## Recommended learning order

1. Reproduce a toy baseline from scratch.
2. Add one controlled intervention.
3. Add one comparison group or ablation.
4. Write a short result summary with limitations.
5. Then move to a paper reproduction or a better-scoped extension.

This is the most useful early-career pattern: small, clear empirical claims, not broad claims about AI safety as a whole.

## Good first notebook structure

- Title and short question
- Sources / paper context
- Prompt set or synthetic dataset
- Baseline vs treatment
- Metrics and plots
- Interpretation and limitations
- Next question

That structure keeps the work public-facing, clean, and easy to explain in applications.
