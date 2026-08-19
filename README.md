# Agent Decision & Cognition

## Purpose

This project studies how Agents make decisions at runtime, what decision-making capability is already present in the model, what system structure adds beyond model capability, and what humans need in order to understand, inspect, question, correct, and accumulate Agent decisions.

The project is **not** intended to define a universal Agent Decision Framework. It is a research project whose architecture should emerge from experiments.

## Core Question

> **Where is the boundary between model capability, system structure, and human cognitive needs?**

More specifically:

1. How much Intent-driven Runtime Decision capability does an LLM already possess?
2. When are Prompt, Context, and Tool descriptions sufficient?
3. When does Runtime Decision provide value over predefined Orchestration, and when is explicit control more reliable?
4. What explicit structures, constraints, observations, capability discovery, or persistence mechanisms remain useful when the model can already decide?
5. How can people understand, inspect, challenge, correct, and accumulate Agent decisions?

## Research Directions

- **A. Intent → Runtime Decision**
- **B. Runtime Decision vs. predefined Orchestration**
- **C. Decision Environment and its observable characteristics**
- **D. Capability Discovery**
- **E. Decision / Alternative / Evidence / Context**
- **F. Memory and Decision boundaries**
- **G. Human-facing representation of Agent Decision**

## Research Principles

- Do not reimplement capabilities the model already has merely because explicit structure is easier to manage.
- Do not confuse observable Agent behavior with an assumed internal model structure.
- Do not assume Runtime Decision or Orchestration is inherently superior; study where decision control belongs and who should exercise it.
- Prefer minimal experiments and ablation/control comparisons before introducing architecture.
- Prefer complete original conversations as research material; avoid selection and summarization that can hide corrections, rejected alternatives, or uncertainty.
- Preserve formation, modification, rejection, preservation, and uncertainty of decisions where observable.
- Preserve Alternatives and Evidence, not only final choices.
- Distinguish **preserve / recall / reason / decide**.
- A Decision Archivist is neutral: it reconstructs and preserves; it does not decide.

## Repository Structure

```text
.
├── README.md
├── AGENTS.md
├── rules/
│   └── research.md
├── research/
│   ├── questions/
│   └── concepts/
├── experiments/
└── findings/
    ├── validated.md
    ├── rejected.md
    └── open-questions.md
```

The repository intentionally starts small. Concepts, schemas, Skills, and other explicit mechanisms should be added only when experiments demonstrate that they are useful.

## Status

Early research / experimental.

The current repository structure is a research scaffold, not a proposed final Agent architecture.
