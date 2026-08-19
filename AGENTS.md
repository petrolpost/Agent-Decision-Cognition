# AGENTS.md

## Project Role

This repository is a research project about **Agent Decision & Cognition**. It is not, by default, an Agent Decision Framework implementation.

The project exists because capable Agents increasingly appear able to make decisions at runtime. That creates a boundary problem: some behavior may already be a model capability, some may be elicited by Prompt and Context, some may come from explicit system structure, and some structures may exist primarily so humans can understand or control what happened.

The purpose of work in this repository is to distinguish:

- model capability;
- prompt/context elicitation;
- system structure and constraints;
- human-facing representation and cognition.

The project asks where decision control should reside, rather than assuming that more orchestration or more autonomy is inherently better.

## Core Research Rules

### 1. Do not assume an explicit Decision object exists inside the model

`Decision`, `Alternative`, `Evidence`, `Context`, and related terms are observational and analytical concepts unless experiments establish a stronger claim. Do not infer internal model structures from useful external representations.

### 2. Do not prematurely replace Runtime Decision with system orchestration

Predefined orchestration is an engineering control mechanism, not a priori an inferior approach. Runtime Decision is likewise a capability to investigate, not a design virtue to assume.

Ask:

- What decision is being made?
- Who or what currently controls it?
- At what point in execution is it controlled?
- What are the reliability, flexibility, observability, and human-control trade-offs?

### 3. Test before architecture

When a proposed component can plausibly be replaced by Prompt, Context, Tool descriptions, or existing Agent mechanisms, test that simpler baseline first.

Prefer:

```text
research question
      ↓
minimal experiment
      ↓
baseline / control
      ↓
observation
      ↓
comparison
      ↓
finding
      ↓
only if justified: concept / Skill / structure
```

over:

```text
concept → schema → framework → implementation
```

### 4. Favor minimal experiments and ablations

When possible, isolate the contribution of:

- model capability;
- prompt elicitation;
- context;
- tool/capability descriptions;
- explicit system structure;
- human-facing representation.

Do not attribute an observed effect to a system mechanism when the experiment cannot distinguish it from prompting or context effects.

### 5. Prefer complete original conversations as research material

For conversational research, use the complete original conversation whenever possible. Do not silently slice, summarize, or select turns in ways that can hide corrections, rejected alternatives, uncertainty, or changes in direction.

The first task is factual reconstruction. Abstraction comes after the evidence is preserved.

### 6. Preserve more than final choices

Where observable and relevant, retain:

- decisions that formed;
- decisions that were modified;
- decisions that were rejected or overridden;
- decisions that were deliberately preserved;
- uncertainty;
- alternatives;
- evidence and its role.

Do not turn a messy runtime process into a clean final answer merely because the final answer is easier to store.

### 7. Keep preserve / recall / reason / decide distinct

A system that stores or retrieves a decision is not necessarily making that decision. A system that reconstructs a decision is not necessarily reasoning about it. Keep these operations conceptually separate until evidence justifies combining them.

### 8. Keep Decision Archivist neutral

A Decision Archivist observes, reconstructs, and preserves. It must not become a Decision Maker merely because its output is useful to a later Agent.

### 9. Separate Agent cognition from human cognition

Do not treat a human-facing representation as evidence that the Agent itself requires the same representation internally.

A structure may be valuable because it helps a human inspect, question, correct, or accumulate Agent behavior even if it provides no runtime benefit to the Agent.

### 10. Use First Class precisely

Use **First Class** to mean that a concept receives complete, direct, natural treatment by the system. It does not mean higher priority or rank.

### 11. Do not design to perfection

The project should evolve through small experiments. A concept that sounds reasonable is a hypothesis, not a requirement for a component.

Prefer a useful imperfect experiment over a complete architecture built on untested assumptions.

## Adding New Structure

Before adding a new directory, schema, Skill, service, or framework abstraction, state:

1. What research question requires it?
2. What simpler baseline was tested?
3. What observation demonstrates that the explicit structure adds value?
4. What alternative explanations remain?
5. Is the proposed structure needed by the Agent, by the system for control/reliability, or primarily by humans for understanding?

If these questions cannot be answered, prefer an experiment or research note over a permanent architecture component.

## Research Artifacts

Keep the roles of repository artifacts distinct:

- `research/introduction.md` explains why the questions exist and provides motivating stories.
- `research/terminology.md` defines the project's current working vocabulary.
- `research/questions/` records questions being investigated.
- `research/concepts/` records working concepts and their evolution; it must not silently turn hypotheses into architecture.
- `experiments/` contains minimal tests, comparisons, and experimental material.
- `findings/` records what experiments support, reject, or leave unresolved.
- `rules/` contains project-wide working rules.

If a Skill or other implementation artifact is created, its existence should be justified by an experiment or a concrete research need. Implementation is evidence-producing instrumentation, not automatically the research conclusion.

## Expected Work Pattern

```text
Question
   ↓
Original evidence / observation
   ↓
Minimal experiment
   ↓
Baseline / control
   ↓
Comparison
   ↓
Finding
   ↓
Only if justified
Concept / Skill / Structure
```
