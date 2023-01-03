---
layout: post
title: Dialectics
description: The Chronicles of Computation, Vol. I
---

[The Chronicles of Computation]({{ site.baseurl }}/#chronicom), Vol. I

## Reception

Experts have been asked to bet social capital on this volume's relevance and usefulness through a brief public review. Should respondents (1) endorse this work when it actually turns out to be irrelevant, or (2) fail to endorse it when it actually turns out to be useful, then they would find themselves in an unfavorable position. Conversely, it would be favorable for them to make qualitative assessments which match reality. This first section can be seen as an experiment on the peer review process inspired by prediction markets, meant to communicate to the reader an assessment of this work's standing informed by experts who are incentivized to weigh in sensibly.

## Summary of contents

In the first half of this volume, we slowly build towards a theoretical framework of language model reasoning centered around dialectics, the age-old practice of truth-seeking through regimented dialogue. In the second half, we attempt to apply the framework by exploring a number of specific use cases in AI safety.{% include sidenote.html id="mn-edges" note='Side notes are used extensively to elaborate on jargon in the volume\'s body, in order to ensure that a broader readership is, both literally and figuratively, on the same page.'%}

### Ch. I, Dialectical Power Dynamics

In the first chapter, we devise an automated way of evaluating parties engaged in a debate of arbitrary length held in natural language. Our algorithm is inspired by the argumentation-theoretic notion of pragmatic validity and the epistemological notion of coherentism, yet its concrete implementation relies on heuristics for node centrality from graph theory.

1. [Kaleidoscope of Validity]()
2. [Algorithm Desiderata]()
3. [ArgRank]()

### Ch. II, Deliberative Arms Race

In the second chapter, we describe in detail the process of obtaining DebateGPT, a language model fine-tuned to simulate increasingly pertinent debates by attempting to maximize the previously described evaluation. This novel training regime incorporates a self-play paradigm, runs mostly on synthetic data, and we assess has a non-zero chance of bootstrapping language model reasoning into superhuman territory, assuming a number of probable future advancements.

1. [Brief Review of Language Models]()
2. [Training DebateGPT]()
3. [Hanson's Elephant]()
4. [Ephemeral Shards & Autocurricular Activities]()
5. [Climbing Schild's Ladder]()

### Ch. III, Bounded Defeasibility 

In the third chapter, we continue by framing the reasoning capabilities of language models such as DebateGPT in terms of _bounded defeasibility_, the amount of computational "firepower" a grouping of arguments can withstand before being invalidated. The amount of time at their disposal, the number of available tries, and the reasoning capabilities of the (simulated) agents in question represent some of those bounds.

1. [Brief Review of Non-Monotonic Logic]()
2. [Argument Is War]()
3. [Core Formalism]()

### Ch. IV, Deployment Strategies 

In the fourth chapter, we then go on to suggest a number of applications of this theoretical framework in AI safety which attempt to unify several recent avenues of investigation: debate, simulators, interpretability, interaction games, long reflection, shard theory, and others. Those deployment strategies are meant to scale in synchrony with the bootstrapped reasoning capabilities hinted at in previous chapters.

1. [Building on Cyborgism]()
2. [Building on Simulators & Metaethics]()
3. [Building on Interaction Games]()
4. [Building on Long Reflection]()
5. [Connections to Logical Inductors]()

### Ch. V, Interdisciplinary Audit

In the fifth and final chapter, we conduct a comprehensive interdisciplinary investigation of DebateGPT, in an attempt to gauge the feasibility of the applications described previously. We approach our object of study from angles as diverse as game theory and dynamical systems.

1. [Argumentation Theory]()
2. [Non-Monotonic Logic]()
3. [Sociology]()
4. [Game Theory]()
5. [Dynamical Systems]()

## Acknowledgements

Paul Bricman would like to thank the [Long-Term Future Fund](https://funds.effectivealtruism.org/funds/far-future) for financial support during the project, [Stability AI](https://stability.ai/) for providing the computational resources necessary to train DebateGPT, and [Conjecture](https://www.conjecture.dev/) for providing the space to explore related ideas during a previous research fellowship, and [AI Safety Camp](https://aisafety.camp/) for providing context and resources for the entire team to investigate DebateGPT.
