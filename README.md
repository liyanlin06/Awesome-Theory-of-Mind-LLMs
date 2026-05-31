# Awesome Theory of Mind for LLMs [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated resource repository for research on **Theory of Mind (ToM)** in Large Language Models and AI systems, maintained as the foundation for a comprehensive survey.

**Theory of Mind** is the cognitive ability to attribute mental states — beliefs, intentions, knowledge, desires, and emotions — to oneself and others, and to understand that others hold states that may differ from one's own. This repository tracks how this capacity is defined, measured, improved, and critiqued in the context of modern AI systems.

## Scope

We include work that addresses **at least one** of the following:
- Evaluating whether LLMs exhibit ToM-related capacities
- Designing benchmarks or datasets to test ToM in AI systems
- Proposing methods to improve ToM performance in LLMs
- Analyzing the mechanisms behind ToM behavior (or failure) in LLMs
- Applying ToM-aware reasoning to downstream tasks

We exclude work focused solely on human cognitive science or developmental psychology unless it directly informs LLM evaluation methodology.

---

## Table of Contents

- [What is Theory of Mind?](#what-is-theory-of-mind)
  - [Core Sub-Abilities](#core-sub-abilities)
  - [Unique Challenges for LLMs](#unique-challenges-for-llms)
- [Benchmarks & Datasets](#benchmarks--datasets)
  - [Text-Only Benchmarks](#text-only-benchmarks)
  - [Multimodal ToM Benchmarks](#multimodal-tom-benchmarks)
- [Methods & Approaches](#methods--approaches)
  - [Prompting-Based](#prompting-based)
  - [Fine-Tuning & Training](#fine-tuning--training)
  - [Neurosymbolic & Modular](#neurosymbolic--modular)
  - [Multi-Agent Frameworks](#multi-agent-frameworks)
- [Analysis & Interpretability](#analysis--interpretability)
  - [Claims of Emergent ToM](#claims-of-emergent-tom)
  - [Critiques & Failure Analysis](#critiques--failure-analysis)
  - [Bias & Social Stereotypes](#bias--social-stereotypes)
  - [Probing Internal Representations](#probing-internal-representations)
- [Applications](#applications)
- [Survey & Position Papers](#survey--position-papers)
- [Star History](#star-history)

---

## What is Theory of Mind?

Theory of Mind was introduced in cognitive science by [Premack & Woodruff (1978)](https://doi.org/10.1017/S0140525X00076512) and operationalized through the *false belief task* by [Wimmer & Perner (1983)](https://doi.org/10.1016/0010-0277(83)90004-5). It describes the capacity to represent others' mental states as distinct from one's own and from reality.

### Core Sub-Abilities

The following taxonomy organizes the papers in this repository. A single paper may cover multiple sub-abilities.

| Tag | Sub-Ability | Description |
|-----|-------------|-------------|
| `[belief]` | **Belief** | Reasoning about what an agent believes, including false beliefs and higher-order beliefs ("A thinks B believes...") |
| `[intention]` | **Intention & Goal** | Inferring what an agent intends to do or is trying to achieve |
| `[knowledge]` | **Knowledge State** | Reasoning about what an agent knows or does not know |
| `[emotion]` | **Emotion & Affect** | Recognizing and reasoning about emotional states |
| `[desire]` | **Desire & Preference** | Inferring what an agent wants or prefers |
| `[perspective]` | **Perspective Taking** | Adopting another agent's viewpoint (visual, spatial, or epistemic) |
| `[deception]` | **Deception & Irony** | Understanding non-literal communication: lies, sarcasm, implicature |
| `[faux-pas]` | **Faux Pas** | Recognizing socially inappropriate statements made from ignorance |

### Unique Challenges for LLMs

- **Benchmark contamination**: Classic ToM tasks (e.g., Sally-Anne) appear in training data, inflating apparent performance
- **Prompt sensitivity**: Small wording changes cause large performance swings, raising questions about robustness
- **Higher-order brittleness**: Models that pass first-order tasks often fail at second- and third-order belief tasks
- **Conflation with language patterns**: Surface co-occurrence statistics may mimic ToM without genuine mental state representation

---

## Benchmarks & Datasets

> Sorted by release date, newest first.

### Text-Only Benchmarks

- **[2026.05]** [**OmniToM: Benchmarking Theory of Mind in LLMs via Explicit Belief Modeling**](https://arxiv.org/abs/2605.26322) [![Paper](https://img.shields.io/badge/arXiv26-b22222)](https://arxiv.org/abs/2605.26322)
  Evaluates belief representations directly via a two-stage pipeline: belief extraction from narrative and seven-dimensional belief labeling. Built on 895 stories with 22,343 labeled belief propositions to probe actor-specific belief-tracking bottlenecks. `[belief]` `[knowledge]` `[perspective]`

- **[2026.04]** [**DialToM: A Theory of Mind Benchmark for Forecasting State-Driven Dialogue Trajectories**](https://arxiv.org/abs/2604.20443) [![Paper](https://img.shields.io/badge/arXiv26-b22222)](https://arxiv.org/abs/2604.20443)
  Evaluates both literal ToM (mental state prediction) and functional ToM (using inferred states to forecast dialogue trajectories). Finds that most LLMs excel at identifying mental states but fail to leverage them for social trajectory prediction. `[belief]` `[intention]` `[desire]`

- **[2025.06]** [**UniToMBench: Integrating Perspective-Taking to Improve Theory of Mind in LLMs**](https://arxiv.org/abs/2506.09450) [![Paper](https://img.shields.io/badge/arXiv25-b22222)](https://arxiv.org/abs/2506.09450)
  Unified benchmark combining multi-interaction tasks and evolving story scenarios, supported by 1,000+ hand-written scenarios; integrates perspective-taking techniques with diverse evaluation metrics. `[belief]` `[emotion]` `[knowledge]`

- **[2025.06]** [**XToM: Exploring the Multilingual Theory of Mind for Large Language Models**](https://arxiv.org/abs/2506.02461) [![Paper](https://img.shields.io/badge/arXiv25-b22222)](https://arxiv.org/abs/2506.02461)
  First rigorously validated multilingual ToM benchmark spanning five languages. Reveals that LLMs' ToM performance varies significantly across languages despite strong multilingual understanding. `[belief]` `[perspective]`

- **[2025.02]** [**PersuasiveToM: A Benchmark for Evaluating Machine Theory of Mind in Persuasive Dialogues**](https://arxiv.org/abs/2502.21017) [![Paper](https://img.shields.io/badge/arXiv25-b22222)](https://arxiv.org/abs/2502.21017) [![Star](https://img.shields.io/github/stars/Yu-Fangxu/PersuasiveToM.svg?style=social&label=Star)](https://github.com/Yu-Fangxu/PersuasiveToM)
  Evaluates ToM in persuasive dialogue via two tasks: tracking evolving desires/beliefs/intentions (ToM Reasoning) and using inferred mental states to predict persuasion strategies (ToM Application). `[belief]` `[desire]` `[intention]`

- **[2025.01]** [**ToMATO: Verbalizing the Mental States of Role-Playing LLMs for Benchmarking Theory of Mind**](https://arxiv.org/abs/2501.08838) [![Paper](https://img.shields.io/badge/AAAI25-B45309)](https://arxiv.org/abs/2501.08838) [![Star](https://img.shields.io/github/stars/nttmdlab-nlp/ToMATO.svg?style=social&label=Star)](https://github.com/nttmdlab-nlp/ToMATO)
  5.4k-question benchmark generated via LLM-LLM conversations with information asymmetry; requires role-playing LLMs to verbalize thoughts before each utterance, capturing first- and second-order mental states across five categories. `[belief]` `[intention]` `[desire]` `[emotion]` `[knowledge]`

- **[2024.12]** [**ExploreToM: Program-Guided Adversarial Data Generation for Theory of Mind Reasoning**](https://arxiv.org/abs/2412.12175) [![Paper](https://img.shields.io/badge/arXiv24-b22222)](https://arxiv.org/abs/2412.12175) [![Star](https://img.shields.io/github/stars/facebookresearch/ExploreToM.svg?style=social&label=Star)](https://github.com/facebookresearch/ExploreToM)
  Uses A* search over a domain-specific language to generate diverse adversarial ToM stories at scale. Addresses contamination by enabling benchmark regeneration; state-of-the-art models score as low as 0–9%. `[belief]`

- **[2024.06]** [**EPITOME: Comparing Humans and Large Language Models on an Experimental Protocol Inventory for Theory of Mind Evaluation**](https://aclanthology.org/2024.tacl-1.45/) [![Paper](https://img.shields.io/badge/TACL24-004488)](https://aclanthology.org/2024.tacl-1.45/)
  Battery of six experiments tapping belief attribution, emotional inference, and pragmatic reasoning; compares five LLMs against a human baseline. Finds LLMs match humans on some tasks but commit systematic errors on pragmatic reasoning requiring mental state integration. `[belief]` `[emotion]` `[knowledge]`

- **[2024.02]** [**OpenToM: A Comprehensive Benchmark for Evaluating Theory-of-Mind Reasoning Capabilities of Large Language Models**](https://arxiv.org/abs/2402.06044) [![Paper](https://img.shields.io/badge/ACL24-004488)](https://arxiv.org/abs/2402.06044) [![Star](https://img.shields.io/github/stars/seacowx/OpenToM.svg?style=social&label=Star)](https://github.com/seacowx/OpenToM)
  Open-ended narrative benchmark with characters having explicit personality traits and intention-driven actions; 696 narratives requiring free-form answers about both physical and psychological world states. `[belief]` `[intention]` `[perspective]`

- **[2024.02]** [**ToMBench: Benchmarking Theory of Mind in Large Language Models**](https://arxiv.org/abs/2402.15052) [![Paper](https://img.shields.io/badge/ACL24-004488)](https://arxiv.org/abs/2402.15052) [![Star](https://img.shields.io/github/stars/zhchen18/ToMBench.svg?style=social&label=Star)](https://github.com/zhchen18/ToMBench)
  Systematic bilingual benchmark with 2,860 samples across 8 tasks and 31 social cognition abilities; built from scratch to avoid data leakage. Even GPT-4 lags behind humans by over 10 percentage points. `[belief]` `[desire]` `[intention]` `[emotion]` `[knowledge]`

- **[2023.10]** [**SOTOPIA: Interactive Evaluation for Social Intelligence in Language Agents**](https://arxiv.org/abs/2310.11667) [![Paper](https://img.shields.io/badge/ICLR24_Spotlight-7C3AED)](https://arxiv.org/abs/2310.11667) [![Star](https://img.shields.io/github/stars/sotopia-lab/sotopia.svg?style=social&label=Star)](https://github.com/sotopia-lab/sotopia)
  Open-ended social simulation environment evaluating LLM agents across 7 dimensions in role-play interactions; also used as a training platform (see SOTOPIA-π). `[intention]` `[desire]` `[knowledge]`

- **[2023.10]** [**Hi-ToM: A Benchmark for Evaluating Higher-Order Theory of Mind Reasoning in Large Language Models**](https://arxiv.org/abs/2310.16755) [![Paper](https://img.shields.io/badge/EMNLP23_Findings-D97706)](https://arxiv.org/abs/2310.16755)
  Tests recursive belief reasoning from 0th to 4th order in narratives with deceptive agents. Reveals sharp performance degradation at 2nd order and above across GPT-4, Claude, and others. `[belief]`

- **[2023.10]** [**FANToM: A Benchmark for Stress-testing Machine Theory of Mind in Interactions**](https://arxiv.org/abs/2310.15421) [![Paper](https://img.shields.io/badge/EMNLP23-D97706)](https://arxiv.org/abs/2310.15421) [![Star](https://img.shields.io/github/stars/skywalker023/fantom.svg?style=social&label=Star)](https://github.com/skywalker023/fantom) [![Project Page](https://img.shields.io/badge/Project_Page-00CED1)](https://hyunw.kim/fantom)
  Conversational ToM benchmark requiring belief tracking across information-asymmetric multi-party dialogues. Introduces multiple question types (BeliefQ, AnswerabilityQ, InfoAccessQ) to detect illusory ToM. `[belief]` `[knowledge]`

- **[2023.06]** [**Understanding Social Reasoning in Language Models with Language Models (BigToM)**](https://arxiv.org/abs/2306.15448) [![Paper](https://img.shields.io/badge/NeurIPS23-166534)](https://arxiv.org/abs/2306.15448)
  Large-scale controlled ToM evaluation using causal graph templates covering percept-to-belief, percept-to-action, and action-to-belief inference. 5,000 LLM-written evaluations designed to resist surface pattern exploitation. `[belief]` `[intention]` `[desire]`

- **[2023.02]** [**Theory of Mind May Have Spontaneously Emerged in Large Language Models**](https://arxiv.org/abs/2302.02083) [![Paper](https://img.shields.io/badge/arXiv23-b22222)](https://arxiv.org/abs/2302.02083)
  Tests GPT models on 40 classic false-belief tasks; GPT-4 solves ~95%, sparking the central debate about emergent ToM in LLMs. Also listed in [Analysis](#claims-of-emergent-tom). `[belief]`

- **[2019.10]** [**ToMi: Revisiting the Evaluation of Theory of Mind through Question Answering**](https://aclanthology.org/D19-1598/) [![Paper](https://img.shields.io/badge/EMNLP19-D97706)](https://aclanthology.org/D19-1598/) [![Star](https://img.shields.io/github/stars/facebookresearch/ToMi.svg?style=social&label=Star)](https://github.com/facebookresearch/ToMi)
  Automatically generated false belief stories based on the Sally-Anne paradigm, covering first- and second-order true/false belief questions. The most widely used baseline benchmark adapted from developmental psychology. `[belief]`

### Multimodal ToM Benchmarks

- **[2026.02]** [**Unveiling the Cognitive Compass: Theory-of-Mind-Guided Multimodal Emotion Reasoning**](https://arxiv.org/abs/2602.00971) [![Paper](https://img.shields.io/badge/ICLR26-7C3AED)](https://arxiv.org/abs/2602.00971) [![Project Page](https://img.shields.io/badge/Project_Page-00CED1)](https://hitemotion.github.io/)
  Introduces HitEmotion, a ToM-grounded hierarchical benchmark diagnosing capability breakpoints across increasing levels of cognitive depth for emotion reasoning. Also proposes a ToM-guided reasoning chain and TMPO (RL with mental states as process-level supervision); see also [Fine-Tuning & Training](#fine-tuning--training). `[emotion]` `[belief]` `[intention]` `[multimodal]`

- **[2025.07]** [**MoMentS: A Comprehensive Multimodal Benchmark for Theory of Mind**](https://arxiv.org/abs/2507.04415) [![Paper](https://img.shields.io/badge/EMNLP25_Findings-D97706)](https://arxiv.org/abs/2507.04415)
  2,300+ MCQA questions grounded in long-form short films with real human actors; evaluates seven ToM categories (Emotions, Non-Literal Communication, Desires, Intentions, Knowledge, Percepts, Beliefs) via facial expressions, gaze, body language, and speech. `[belief]` `[intention]` `[desire]` `[emotion]` `[multimodal]`

- **[2024.08]** [**MuMA-ToM: Multi-modal Multi-Agent Theory of Mind**](https://arxiv.org/abs/2408.12574) [![Paper](https://img.shields.io/badge/AAAI25_Oral-B45309)](https://arxiv.org/abs/2408.12574) [![Star](https://img.shields.io/github/stars/SCAI-JHU/MuMA-ToM.svg?style=social&label=Star)](https://github.com/SCAI-JHU/MuMA-ToM) [![Project Page](https://img.shields.io/badge/Project_Page-00CED1)](http://scai.cs.jhu.edu/projects/MuMA-ToM/)
  First multi-modal multi-agent ToM benchmark; provides video and text descriptions of people's behavior in realistic household environments, then asks about goals, beliefs, and beliefs about others' goals. Proposes LIMP (Language model-based Inverse Multi-agent Planning), significantly outperforming GPT-4o and Gemini-1.5 Pro. `[belief]` `[intention]` `[multimodal]` `[multi-agent]`

- **[2024.01]** [**MMToM-QA: Multimodal Theory of Mind Question Answering**](https://arxiv.org/abs/2401.08743) [![Paper](https://img.shields.io/badge/ACL24_Outstanding-004488)](https://arxiv.org/abs/2401.08743) [![Star](https://img.shields.io/github/stars/chuanyangjin/MMToM-QA.svg?style=social&label=Star)](https://github.com/chuanyangjin/MMToM-QA)
  First multimodal ToM benchmark; 600 questions (belief + goal inference) grounded in videos of people searching for household objects. Introduces BIP-ALM combining Bayesian inverse planning with LLMs. `[belief]` `[intention]` `[multimodal]`

---

## Methods & Approaches

> Sorted by release date, newest first.

### Prompting-Based

- **[2025.01]** [**Decompose-ToM: Enhancing Theory of Mind Reasoning in Large Language Models through Simulation and Task Decomposition**](https://arxiv.org/abs/2501.09056) [![Paper](https://img.shields.io/badge/COLING25-0F766E)](https://arxiv.org/abs/2501.09056)
  Decomposes ToM into recursive perspective simulation and granular statement-awareness subtasks; improves performance on higher-order and conversational ToM tasks with no additional training. `[belief]` `[perspective]`

- **[2024.07]** [**TimeToM: Temporal Space is the Key to Unlocking the Door of Large Language Models' Theory-of-Mind**](https://arxiv.org/abs/2407.01455) [![Paper](https://img.shields.io/badge/arXiv24-b22222)](https://arxiv.org/abs/2407.01455)
  Constructs a temporal space with timelines and Temporal Belief State Chains (TBSC) per character; a belief solver transforms higher-order beliefs into first-order beliefs under belief communication. `[belief]` `[knowledge]`

- **[2023.11]** [**Think Twice: Perspective-Taking Improves Large Language Models' Theory-of-Mind Capabilities (SimToM)**](https://arxiv.org/abs/2311.10227) [![Paper](https://img.shields.io/badge/ACL24-004488)](https://arxiv.org/abs/2311.10227) [![Star](https://img.shields.io/github/stars/shawnsihyunlee/simulatedtom.svg?style=social&label=Star)](https://github.com/shawnsihyunlee/simulatedtom)
  Two-stage prompting: Stage 1 filters context to only events a character has witnessed; Stage 2 answers the ToM question from that constrained perspective. Outperforms zero-shot and CoT without fine-tuning. `[belief]` `[perspective]`

- **[2023.06]** [**Minding Language Models' (Lack of) Theory of Mind: A Plug-and-Play Multi-Character Belief Tracker (SymbolicToM)**](https://arxiv.org/abs/2306.00924) [![Paper](https://img.shields.io/badge/ACL23-004488)](https://arxiv.org/abs/2306.00924) [![Star](https://img.shields.io/github/stars/msclar/symbolictom.svg?style=social&label=Star)](https://github.com/msclar/symbolictom)
  Constructs explicit symbolic graphical representations of each character's belief states, then queries the LLM against the belief graph zero-shot. Achieves strong out-of-distribution performance on ToMi. `[belief]`

### Fine-Tuning & Training

- **[2026.02]** [**Unveiling the Cognitive Compass: Theory-of-Mind-Guided Multimodal Emotion Reasoning**](https://arxiv.org/abs/2602.00971) [![Paper](https://img.shields.io/badge/ICLR26-7C3AED)](https://arxiv.org/abs/2602.00971) [![Project Page](https://img.shields.io/badge/Project_Page-00CED1)](https://hitemotion.github.io/)
  TMPO uses intermediate mental states as process-level RL supervision to guide and strengthen multimodal emotion reasoning; also listed under [Multimodal ToM Benchmarks](#multimodal-tom-benchmarks) for the HitEmotion benchmark. `[emotion]` `[belief]` `[multimodal]`

- **[2024.12]** [**ExploreToM: Program-Guided Adversarial Data Generation for Theory of Mind Reasoning**](https://arxiv.org/abs/2412.12175) [![Paper](https://img.shields.io/badge/arXiv24-b22222)](https://arxiv.org/abs/2412.12175) [![Star](https://img.shields.io/github/stars/facebookresearch/ExploreToM.svg?style=social&label=Star)](https://github.com/facebookresearch/ExploreToM)
  Fine-tuning on ExploreToM-generated adversarial data yields a 27-point accuracy improvement on ToMi; also listed under [Benchmarks](#llm-specific-benchmarks). `[belief]`

- **[2024.03]** [**SOTOPIA-π: Interactive Learning of Socially Intelligent Language Agents**](https://arxiv.org/abs/2403.08715) [![Paper](https://img.shields.io/badge/ACL24-004488)](https://arxiv.org/abs/2403.08715) [![Star](https://img.shields.io/github/stars/sotopia-lab/sotopia-pi.svg?style=social&label=Star)](https://github.com/sotopia-lab/sotopia-pi)
  Interactive learning within the SOTOPIA environment using behavior cloning and self-reinforcement to improve social intelligence, including ToM-relevant social reasoning. `[intention]` `[desire]` `[knowledge]`

### Neurosymbolic & Modular

- **[2025.03]** [**EnigmaToM: Improve LLMs' Theory-of-Mind Reasoning Capabilities with Neural Knowledge Base of Entity States**](https://arxiv.org/abs/2503.03340) [![Paper](https://img.shields.io/badge/ACL25_Findings-004488)](https://arxiv.org/abs/2503.03340)
  Neuro-symbolic framework integrating a Neural Knowledge Base (Enigma) for psychology-inspired iterative masking and knowledge injection; constructs spatial scene graphs for belief tracking. Significantly improves higher-order ToM reasoning across model sizes. `[belief]` `[knowledge]` `[perspective]`

### Multi-Agent Frameworks

- **[2025.09]** [**Infusing Theory of Mind into Socially Intelligent LLM Agents (ToMAgent)**](https://arxiv.org/abs/2509.22887) [![Paper](https://img.shields.io/badge/arXiv25-b22222)](https://arxiv.org/abs/2509.22887)
  Introduces ToMAgent (ToMA), trained by pairing ToM with dialogue lookahead to produce mental states maximally useful for achieving dialogue goals; demonstrates more strategic, goal-oriented reasoning on SOTOPIA. `[intention]` `[desire]` `[belief]` `[multi-agent]`

- **[2023.10]** [**Theory of Mind for Multi-Agent Collaboration via Large Language Models**](https://arxiv.org/abs/2310.10701) [![Paper](https://img.shields.io/badge/EMNLP23-D97706)](https://arxiv.org/abs/2310.10701) [![Star](https://img.shields.io/github/stars/romanlee6/multi_LLM_comm.svg?style=social&label=Star)](https://github.com/romanlee6/multi_LLM_comm)
  Evaluates LLM agents in cooperative text games with explicit ToM inference tasks; finds emergent collaborative behaviors but also reveals planning failures from long-context hallucination. `[belief]` `[intention]` `[multi-agent]`

---

## Analysis & Interpretability

> Sorted by release date, newest first.

### Claims of Emergent ToM

- **[2023.02]** [**Theory of Mind May Have Spontaneously Emerged in Large Language Models**](https://arxiv.org/abs/2302.02083) [![Paper](https://img.shields.io/badge/arXiv23-b22222)](https://arxiv.org/abs/2302.02083)
  Kosinski (2023): GPT-4 solves 95% of classic false-belief tasks — equivalent to adult human performance — interpreted as evidence of ToM spontaneously emerging as a byproduct of language modeling. `[belief]`

### Critiques & Failure Analysis

- **[2024.12]** [**Position: Theory of Mind Benchmarks are Broken for Large Language Models**](https://arxiv.org/abs/2412.19726) [![Paper](https://img.shields.io/badge/ICML25_Position-0369A1)](https://arxiv.org/abs/2412.19726)
  Distinguishes *literal* ToM (predicting others' behavior) from *functional* ToM (adapting to agents in-context). Finds that current benchmarks only test the former; most LLMs still fail at functional ToM despite strong literal performance. `[belief]` `[intention]`

- **[2023.02]** [**Large Language Models Fail on Trivial Alterations to Theory-of-Mind Tasks**](https://arxiv.org/abs/2302.08399) [![Paper](https://img.shields.io/badge/arXiv23-b22222)](https://arxiv.org/abs/2302.08399)
  Ullman (2023): Small, semantically irrelevant variations to classic ToM stories (e.g., making containers transparent, adding truthful testimony) cause GPT-4 to fail catastrophically, suggesting pattern matching rather than genuine reasoning. `[belief]`

### Bias & Social Stereotypes

- **[2025.06]** [**MIST: Towards Multi-dimensional Implicit BiaS Evaluation of LLMs for Theory of Mind**](https://arxiv.org/abs/2506.14161) [![Paper](https://img.shields.io/badge/arXiv25-b22222)](https://arxiv.org/abs/2506.14161)
  Reconceptualizes implicit stereotypes in LLMs as multi-dimensional ToM failures across competence, sociability, and morality; introduces two indirect tasks (WABT and AAT) to uncover latent biases without triggering model avoidance. `[belief]` `[emotion]` `[intention]`

### Probing Internal Representations

- **[2024.02]** [**Language Models Represent Beliefs of Self and Others**](https://arxiv.org/abs/2402.18496) [![Paper](https://img.shields.io/badge/ICML24-0369A1)](https://arxiv.org/abs/2402.18496) [![Star](https://img.shields.io/github/stars/Walter0807/RepBelief.svg?style=social&label=Star)](https://github.com/Walter0807/RepBelief)
  Trains linear probes on LLM activations to decode agents' belief states; finds that belief representations exist internally and causally affect ToM task performance when manipulated. `[belief]` `[knowledge]`

---

## Applications

> Sorted by release date, newest first.

- **[2025.09]** [**Infusing Theory of Mind into Socially Intelligent LLM Agents (ToMAgent)**](https://arxiv.org/abs/2509.22887) [![Paper](https://img.shields.io/badge/arXiv25-b22222)](https://arxiv.org/abs/2509.22887)
  Dialogue agent trained with ToM-aware lookahead; achieves more strategic, long-horizon adaptive reasoning on SOTOPIA. Also listed under [Multi-Agent Frameworks](#multi-agent-frameworks). `[intention]` `[desire]` `[belief]`

- **[2025.05]** [**ToMAP: Training Opponent-Aware LLM Persuaders with Theory of Mind**](https://arxiv.org/abs/2505.22961) [![Paper](https://img.shields.io/badge/arXiv25-b22222)](https://arxiv.org/abs/2505.22961) [![Star](https://img.shields.io/github/stars/ulab-uiuc/ToMAP.svg?style=social&label=Star)](https://github.com/ulab-uiuc/ToMAP)
  Uses ToM modules to track opponent mental states during persuasion; a 3B-parameter model trained with RL outperforms GPT-4o by 39.4% across diverse persuadee models. `[belief]` `[desire]` `[intention]`

- **[2024.05]** [**LLM Theory of Mind and Alignment: Opportunities and Risks**](https://arxiv.org/abs/2405.08154) [![Paper](https://img.shields.io/badge/arXiv24-b22222)](https://arxiv.org/abs/2405.08154)
  Position paper on the dual-use nature of ToM: enables conversational adaptation and empathy at the individual level, but can facilitate agent collusion, deception, and privacy breaches at the group level. `[intention]` `[desire]` `[emotion]`

- **[2024.01]** [**Theory of Mind Abilities of Large Language Models in Human-Robot Interaction: An Illusion?**](https://arxiv.org/abs/2401.05302) [![Paper](https://img.shields.io/badge/arXiv24-b22222)](https://arxiv.org/abs/2401.05302)
  LLMs score well on vanilla HRI prompts but fail the invariance requirements of true ToM under minor perturbations — suggesting apparent ability is an illusion in embodied interaction settings. `[belief]` `[intention]` `[perspective]`

- **[2023.10]** [**SOTOPIA: Interactive Evaluation for Social Intelligence in Language Agents**](https://arxiv.org/abs/2310.11667) [![Paper](https://img.shields.io/badge/ICLR24_Spotlight-7C3AED)](https://arxiv.org/abs/2310.11667) [![Star](https://img.shields.io/github/stars/sotopia-lab/sotopia.svg?style=social&label=Star)](https://github.com/sotopia-lab/sotopia)
  Open-ended social simulation environment; reveals that GPT-4 still falls short of humans on goal completion and social commonsense reasoning across diverse role-play scenarios. `[intention]` `[desire]` `[knowledge]`

- **[2023.10]** [**Theory of Mind for Multi-Agent Collaboration via Large Language Models**](https://arxiv.org/abs/2310.10701) [![Paper](https://img.shields.io/badge/EMNLP23-D97706)](https://arxiv.org/abs/2310.10701) [![Star](https://img.shields.io/github/stars/romanlee6/multi_LLM_comm.svg?style=social&label=Star)](https://github.com/romanlee6/multi_LLM_comm)
  Explicit belief state representations enhance task performance and ToM inference accuracy in cooperative multi-agent text games; reveals planning failures from long-context hallucination. `[belief]` `[intention]` `[multi-agent]`

- **[2023.06]** [**MindDial: Belief Dynamics Tracking with Theory-of-Mind Modeling for Situated Neural Dialogue Generation**](https://arxiv.org/abs/2306.15253) [![Paper](https://img.shields.io/badge/SIGDIAL24-6B7280)](https://arxiv.org/abs/2306.15253)
  Dialogue framework with an explicit mind module tracking first- and second-order beliefs to resolve belief differences and achieve common ground alignment and negotiation. `[belief]` `[knowledge]`

---

## Survey & Position Papers

- **[2025.02]** [**A Survey of Theory of Mind in Large Language Models: Evaluations, Representations, and Safety Risks**](https://arxiv.org/abs/2502.06470) [![Paper](https://img.shields.io/badge/arXiv25-b22222)](https://arxiv.org/abs/2502.06470)
  Comprehensive survey covering behavioral and representational ToM evaluation, safety risks from advanced LLM ToM, and future research directions.

- **[2023.10]** [**Towards A Holistic Landscape of Situated Theory of Mind in Large Language Models**](https://arxiv.org/abs/2310.19619) [![Paper](https://img.shields.io/badge/EMNLP23_Findings-D97706)](https://arxiv.org/abs/2310.19619)
  Taxonomizes machine ToM into 7 mental state categories following psychological studies; systematically reviews existing benchmarks to identify under-explored aspects and argues for situated evaluation where LLMs are both physically and socially situated agents.

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=liyanlin06/Awesome-Theory-of-Mind-LLM&type=Date)](https://star-history.com/#YOUR_USERNAME/awesome-llm-theory-of-mind&Date)
