---
layout: post
title: Dialectics
description: The Chronicles of Computation, Vol. I
---

[The Chronicles of Computation]({{ site.baseurl }}/#chronicom), Vol. I

**This document is currently a work in progress. Please refrain from sharing it before it gets published, for ensuring an optimal reading experience.**

## Reception

Experts have been asked to bet social capital on this volume's relevance and usefulness through a brief public review. Should respondents (1) endorse this work when it actually turns out to be irrelevant, or (2) fail to endorse it when it actually turns out to be useful, then they would find themselves in an unfavorable position. Conversely, it would be favorable for them to make qualitative assessments which match reality. This first section can be seen as a spin on the peer review process inspired by prediction markets, meant to communicate to the reader an assessment of this work's standing informed by experts who are incentivized to weigh in sensibly.

## Summary of contents

In the first half of this volume, we slowly build towards a theoretical framework of language model reasoning centered around dialectics, the age-old practice of truth-seeking through regimented dialogue. In the second half, we attempt to apply the framework by exploring a number of specific use cases in AI safety.{% include sidenote.html id="mn-sidenotes" note='Side notes are used extensively to elaborate on jargon in the volume\'s body, in order to ensure that a broader readership is, both literally and figuratively, on the same page.'%}

### Ch. I, Dialectical Power Dynamics

In the first chapter, we devise an automated way of evaluating parties engaged in a debate of arbitrary length held in natural language. Our algorithm is inspired by the argumentation-theoretic notion of pragmatic validity and the epistemological notion of coherentism, yet its concrete implementation relies on heuristics for node centrality from graph theory.

1. [Kaleidoscope of Reasonableness]()
2. [Reasoning & Belief]()
3. [Algorithm Desiderata]()
4. [ArgRank]()

### Ch. II, Deliberative Arms Race

In the second chapter, we describe in detail the process of obtaining DebateGPT, a language model fine-tuned to simulate increasingly pertinent debates by attempting to excel at the previously described evaluation. This novel training regime incorporates a self-play paradigm, runs mostly on synthetic data, and we assess has a non-zero chance of bootstrapping language model reasoning into superhuman territory, assuming a number of probable future advancements.

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

Paul Bricman would like to thank the [Long-Term Future Fund](https://funds.effectivealtruism.org/funds/far-future) for financial support during the project, [Stability AI](https://stability.ai/) for providing the computational resources necessary to train DebateGPT, [Conjecture](https://www.conjecture.dev/) for providing the space to explore related ideas during a previous research fellowship, and [AI Safety Camp](https://aisafety.camp/) for providing context and resources for the entire team to investigate DebateGPT.

## Ch. I, Dialectical Power Dynamics

### Kaleidoscope of Reasonableness

Ask a scholar of pure mathematics, computer science, or formal logic what makes an instance of argumentation valid, and they will likely highlight the relevance of making sure that the conclusion follows logically from the premises for each individual reasoning step. More often than not, this implies relying on a host of approved inference types, while making sure to steer clear of degenerate ones (i.e. fallacies). This conception of reasonableness is often referred to as "geometrical," due to its appeal to only build on solid premises and construct arguments using an idealized set of operations.

Ask a scholar of argumentation theory the same question, and—following a cursory smile indicating they have long been waiting for this—they will likely not hesitate to point out that there have been multiple prominent schools of thought over time which advocated different, often incompatible, conceptions of reasonableness. Each one is backed by a different rationale, has its own features and shortcomings, and has emerged in a different cultural setting, often separated by thousands of years and kilometers. Let us briefly sample this range of conceptions.

For instance, Perelman and Olbrechts-Tyteca suggested a conception of reasonableness grounded in rhetoric. According to it, an instance of argumentation is valid if and only if it succeeds in persuading a group of individuals of its conclusion. While the most visible shortcoming of this conception is that it can quickly degenerate into sophism,{% include sidenote.html id="mn-sophism" note='The sophists were teachers of rhetoric in ancient Greece, notorious for "equipping" individuals with techniques for making a strong case in court, regardless of the appropriateness of their position. Being sneered at by virtually all their contemporary philosophers, they were frowned upon for not seeking wisdom, but merely monetizing the skill of persuasion as a means of taking advantage of others.'%} its proponents highlight the possibility of grounding reasonableness in the persuasion of a particularly _rational_ audience. This litmus test can be further extended to involve the persuasion of an idealized omniscient agent, but also of oneself, by framing self-deliberation as self-persuasion.

<div class='epigraph'><blockquote><p>Indeed, the object of the theory of argumentation is the study of the discursive techniques allowing us to induce or to increase the mind's adherence to the theses presented for its assent.</p>
<footer>Chaïm Perelman & Lucie Olbrechts-Tyteca,<cite> The New Rhetoric: A Treatise on Argumentation</cite></footer></blockquote></div>

As a different example, Toulmin and the school of thought which emerged around his ideas advocated for a conception of reasonableness which incorporates domain-specificity. If the geometrical conception often requires abstracting statements into propositional atoms (i.e. $$P$$ could equally well denote _"All men are mortal."_ and _"Socrates is a man."_), Toulmin argues that arguments are often _substantial_, relying on domain-specific means of warranting conclusions, as opposed to standardized  _analytical_ operations on abstracted symbols. For instance, the fact that a study in the natural sciences has conformed to best practices in terms of replicability and reprodicibility can be used to back its findings. In contrast, people working in pure mathematics might not rely on peer-reviewed empirical studies to back theorems, but might want to verify proofs using software. The practices of ensuring sound reasoning in finance are yet again different, relying more on computer simulations and historical performance. Several spin-off schools of thought echoed Toulmin's dissatisfaction regarding the limited practical reach of the highly-analytical formal logic, including the slightly chaotic field of _informal logic_.

<div class='epigraph'><blockquote><p>A man demonstrates his rationality, not by a commitment to fixed ideas, stereotyped procedures, or immutable concepts, but by the manner in which, and the occasions on which, he changes those ideas, procedures, and concepts.</p>
<footer>Stephen Toulmin,<cite> Human Understanding</cite></footer></blockquote></div>

To expand our collection of reasonableness conceptions even further, the pragma-dialectical framework developed by van Eemeren and Grootendorst grounds reasonableness in dialectics. In this context, an instance of argumentation is valid if and only if there exists no strategy to be employed by an opponent in a regimented dialogue which manages to undermine it. The proponents of this framework are particularly interested in enabling effective reasoning in a wide range of situations, rather than only in some higher realm of abstractions. That is why the conception of reasonableness on which their framework rests has a major pragmatic component. The regimented dialogue can be carried out by real individuals and can target a wide range of matters, from the most mundane to the most consequential. The ruleset of available tactics is simply made available to the individuals engaged in dialogue at the beginning, while strategies can be as diverse as forcing the opponent into self-contradiction or exploiting their (involuntary) support. That said, the framework can be brought closer to formal dialectics in order to account for idealized reasoning by employing perfectly rational agents as discussants, in a move similar to that of Perelman and Olbrechts-Tyteca.

<div class='epigraph'><blockquote><p>Accordingly, the prime aims of the present discussion are to exhibit the sociocommunal roots of the foundations of rationality, to provide an instrument for the critique of scepticism implicit in the cognitive solipsism of the Cartesian approach, and to illuminate the communal and controversy-oriented aspects of argumentation and inquiry—scientiﬁc inquiry in particular.</p>
<footer>Nicholas Rescher,<cite> Dialectics</cite></footer></blockquote></div>

Indeed, for many centuries at a time, logic has been but part of dialectics, rather than a field of its own.{% include sidenote.html id="mn-ma" note='For instance, during the Middle Ages. Refer to _Section 2.10.1_ of the [Handbook of Argumentation Theory](https://link.springer.com/referencework/10.1007/978-90-481-9473-5) for a more detailed account.'%} The hot and cold relationship of the two disciplines over the centuries has perhaps been the closest thing argumentation theory has ever had to juicy gossip, with rhetoric a controversial element to complete the triad. It is difficult to overstate the reliance of contemporary mathematics, both pure and applied, on the foundation of formal logic, and so the very idea of scholars erecting an edifice on a different foundation tends to induce vertigo. The very possibility of notions as elementary as conjunction, disjunction, and negation to be defined on the basis of a regimented dialogue instead of a logic{% include sidenote.html id="mn-ma" note='The term _logic_ is used here as countable in reference to the broad range of [three-valued](https://en.wikipedia.org/wiki/Three-valued_logic), [four-valued](https://en.wikipedia.org/wiki/Four-valued_logic), [many-valued](https://en.wikipedia.org/wiki/Many-valued_logic), and [modal](https://en.wikipedia.org/wiki/Modal_logic) logics which compete with [classical two-valued logic](https://en.wikipedia.org/wiki/Classical_logic).'%} sounds exceedingly exotic to the contemporary ear, outside a handful of niches like ludics, game semantics, and interactive computation.

To bring this section to an end, we have completed a very brief tour of several conceptions of reasonableness with the purpose of highlighting the breadth of approaches devised by scholars through the ages. Determining which conception of reasonableness is itself more reasonable is the subject of vigorous debate in present-day argumentation theory. Each conception appears better suited to deal with certain aspects of argumentation, while lacking in other respects. In the rest of this chapter, we will build on top of many of the conceptions listed above, in an attempt to develop an automated pipeline for estimating reasonableness as a single floating-point number.

### Reasoning & Belief
