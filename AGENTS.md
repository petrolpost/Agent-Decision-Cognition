# AGENTS.md

## Project Role

This repository is a research project about Agent Decision & Cognition. It is not, by default, an Agent Decision framework implementation.

The purpose of work in this repository is to distinguish:

- model capability;
- prompt/context elicitation;
- system structure and constraints;
- human-facing representation and cognition.

## Core Research Rules

### 1. Do not assume an explicit Decision object exists inside the model

`Decision`, `Alternative`, `Evidence`, `Context`, and related terms are observational and analytical concepts unless experiments establish a stronger claim. Do not infer internal model structures from useful external representations.

### 2. Do not prematurely replace Runtime Decision with system orchestration

Predefined orchestration is an engineering control mechanism, not a priori an inferior approach. Compare where decision control resides and what trade-offs result.

### 3. Test before architecture

When a proposed component can plausibly be replaced by Prompt, Context, Tool descriptions, or existing Agent mechanisms, test that simpler baseline first.

Prefer:

```text
baseline → controlled change → observation → comparison → finding
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

### 5. Preserve the original decision process

For conversational research, prefer the complete original conversation as the source corpus. Do not silently remove corrections, rejected alternatives, uncertainty, or intermediate reasoning that is relevant to the research question.

### 6. Preserve more than final choices

Where observable and relevant, retain:

- decisions that formed;
- decisions that were modified;
- decisions that were rejected or overridden;
- decisions that were deliberately preserved;
- uncertainty;
- alternatives;
- evidence and its role.

### 7. Keep preserve / recall / reason / decide distinct

A system that stores or retrieves a decision is not necessarily making that decision. A system that reconstructs a decision is not necessarily reasoning about it. Keep these operations conceptually separate until evidence justifies combining them.

### 8. Keep Decision Archivist neutral

A Decision Archivist observes, reconstructs, and preserves. It must not become a Decision Maker merely because its output is useful to a later Agent.

### 9. Use First Class precisely

Use **First Class** to mean that a concept receives complete, direct, natural treatment by the system. It does not mean higher priority or rank.

### 10. Do not design to perfection

The project should evolve through small experiments. A concept that sounds reasonable is a hypothesis, not a requirement for a component.

## Adding New Structure

Before adding a new directory, schema, Skill, service, or framework abstraction, state:

1. What research question requires it?
2. What simpler baseline was tested?
3. What observation demonstrates that the explicit structure adds value?
4. What alternative explanations remain?

If these questions cannot be answered, prefer an experiment or research note over a permanent architecture component.

## Expected Work Pattern

```text
Research Question
      ↓
Minimal Experiment
      ↓
Baseline / Control
      ↓
Observation
      ↓
Finding
      ↓
Only if justified: Concept / Skill / Structure
```
