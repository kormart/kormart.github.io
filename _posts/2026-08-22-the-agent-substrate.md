---
layout: post
title: "The Agent Substrate"
date: 2026-08-22 12:00:00 -0000
categories: coding ai
---

Just as I'm about to publish this post, I notice this thought-provoking piece about harness evolution [16], that I just have to include, I'll come back to it later.

Recently, there is an emphasis on the mechanisms that sit between a generative AI model and the users: the harness. Harness engineering is a thing [1]. Also, a lot of focus is being put on *code* as the dominating tool and output modality. If we put in the additional idea that the generated code is more of a substrate for achieving an outcome, instead of being the output itself, then we have the ingedients of a recent extensive survey paper "Code as Agent Harness" [2].

One particular direction is to give the harness an interactive, REPL-like, code runtime. The symbolic world model is then the instantiated runtime objects in that runtime. For example, the world model is the set of Python runtime objects in the case where the runtime is an IPython kernel. The harness is in control of the execution (runtime state) of the code, not only the source code itself.

An early paper in this direction is WorldCoder [3], which builds on earlier work on program synthesis, e.g., DreamCoder [4]. Another project with a similar publication date is CodeAct [5]. As for startup projects building on these ideas, both Symbolica/Agentica [6] and Marimo [7] are spearheads.

Over the summer weeks of 2026, we have seen several new projects in this "REPL-harness" direction.

- DreamTeam [8] focuses on having specific roles within the harness that contribute to updating the code that is the world model. NOOA [9] is a scaled down version of DreamTeam. Both are open source.

- Schema-harness [10] is focused on separating the state variables and the state transition logic in the code world model. We have not yet seen open source for this project.

- Prime Agent [11] is more of a general purpose agent, based on the pi-harness, using an IPython kernel as the runtime, and building on RLM [12] and Continual Harness [13]. It is open source.

- Tycho [14] is an academic project that has a Moore machine as a representation for the harness side of the agent. It is also open source.

The ARC-AGI-3 challenge [15] is a target benchmark for many of these projects. ARC-AGI-3 puts focus on agents solving for an outcome by interacting with a graphical interface. All these code executing harnesses get scores that are significantly higher compared to the bare models. It seems that the principle of having code as the world model is what makes the difference.

Comparing these projects would be interesting, for example: how is the code executed and how are code updates constructed. And also to benchmark on more practical tasksets than ARG-AGI-3.

Also, there is a taxonomy question here: Is it useful to include all aspects of this executable code world model in the term harness? Most of the projects use the term harness that way.

A proposal would be to distinguish between: 1) the Substrate: the parts that is the representation of the world model (getting updated as part of the session) and 2) the Harness: the interface between the AI model and the world model. The Substrate can contain more than code, including any kind of data, retrieval techniques, memory, ontologies, skills, and specifications. The Harness is the immutable control point for security, cost control, model routing etc.

Instead of defining the Model, Harness, and the Substrate by exactly what they contain, it could be useful to see them more along a temporal axis. The Model is what gets updated at training time, the Substrate is what gets updated at runtime, and the Harness is what gets updated at build time. The Harness then gets a specific role as the part that is not touchable by the Model, which is essential for a robust security level.

Having code as the world model has an impact on how we should think about explainability and interpretability. Code, being symbolic, is easier to analyze, test, perform formal methods on, compared to the latent space of the Model.


### References

[1] Lilian Weng, [Harness Engineering for Self-Improvement](https://lilianweng.github.io/posts/2026-07-04-harness/), 4 July 2026.

[2] "Code as Agent Harness: Toward Executable, Verifiable, and Stateful Agent Systems". arXiv:2605.18747.

[3] Hao Tang, Darren Key, Kevin Ellis, [WorldCoder, a Model-Based LLM Agent: Building World Models by Writing Code and Interacting with the Environment](https://arxiv.org/abs/2402.12275), NeurIPS 2024. arXiv:2402.12275.

[4] Kevin Ellis, Catherine Wong, Maxwell Nye, Mathias Sablé-Meyer, Luc Cary, Lucas Morales, Luke Hewitt, Armando Solar-Lezama, Joshua B. Tenenbaum, [DreamCoder: Growing generalizable, interpretable knowledge with wake-sleep Bayesian program learning](https://arxiv.org/abs/2006.08381), 2020. arXiv:2006.08381.

[5] Xingyao Wang, Yangyi Chen, Lifan Yuan, Yizhe Zhang, Yunzhu Li, Hao Peng, Heng Ji, [Executable Code Actions Elicit Better LLM Agents](https://arxiv.org/abs/2402.01030), ICML 2024 (PMLR 235). arXiv:2402.01030. (Introduces the CodeAct agent.) Code: [github.com/xingyaoww/code-act](https://github.com/xingyaoww/code-act)

[6] Symbolica, [Agentica SDK](https://docs.symbolica.ai/) (documentation), and [SotA ARC-AGI-2 Results with REPL Agents](https://www.symbolica.ai/blog/arcgentica) (blog). Reference implementation: [github.com/symbolica-ai/arcgentica](https://github.com/symbolica-ai/arcgentica)

[7] marimo, [Introducing marimo pair](https://marimo.io/blog/marimo-pair), 7 April 2026.

[8] Elad Sarafian, Gal Kaplun, Ron Banner, Daniel Soudry, Boris Ginsburg (NVIDIA; Soudry also Technion), [Workspace Optimization: How to Train Your Agent](https://arxiv.org/abs/2605.09650), 10 May 2026. arXiv:2605.09650. (Introduces the DreamTeam agent.)

[9] Ricardo Silveira Cabral, Paul Furgale, [Six Agent Harness Capabilities for Higher Model Performance](https://developer.nvidia.com/blog/six-agent-harness-capabilities-for-higher-model-performance/), NVIDIA Technical Blog, 27 July 2026. Code: [github.com/nvidia-nemo/labs-OO-Agents](https://github.com/nvidia-nemo/labs-OO-Agents)

[10] Schema, [Frontier Models with Our Harness Achieve ~99% on ARC-AGI-3 Public](https://schema-harness.github.io/). (results self-reported; not open source)

[11] Prime Intellect, [Prime Agent](https://www.primeintellect.ai/blog/prime-agent), 5 August 2026.

[12] [Recursive Language Models](https://arxiv.org/abs/2512.24601), arXiv:2512.24601. See also Prime Intellect, [Recursive Language Models: the paradigm of 2026](https://www.primeintellect.ai/blog/rlm).

[13] Seth Karten, Joel Zhang, Tersoo Upaa Jr, Ruirong Feng, Wenzhe Li, Chengshuai Shi, Chi Jin, Kiran Vodrahalli, [Continual Harness: Online Adaptation for Self-Improving Foundation Agents](https://arxiv.org/abs/2605.09998), 11 May 2026. arXiv:2605.09998. Code: [github.com/sethkarten/continual-harness](https://github.com/sethkarten/continual-harness)

[14] [Tycho: Active Abstraction with Programmatic World Models for ARC-AGI-3](https://arxiv.org/abs/2607.28287), arXiv:2607.28287. Code: [github.com/NIMI-research/Tycho](https://github.com/NIMI-research/Tycho)

[15] ARC Prize Foundation, [ARC-AGI-3: A New Challenge for Frontier Agentic Intelligence](https://arcprize.org/arc-agi/3) ([technical report](https://arcprize.org/media/ARC_AGI_3_Technical_Report.pdf)) and the [ARC Prize 2026 competition](https://arcprize.org/competitions/2026/arc-agi-3).

[16] [The Evolution of the Agent Harness](https://www.latent.space/p/attention-interface), August 22.
