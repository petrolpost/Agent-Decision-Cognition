# Agent Decision & Cognition

> **What does the Agent already know how to decide, what does the system still need to decide for it, and what does the human need to see even when neither the Agent nor the system needs it to act?**

## Why this project exists

An Agent is asked:

> “I have a customer meeting tomorrow. Help me prepare.”

A conventional system can turn this into a workflow: gather the customer profile, inspect recent activity, search the product history, prepare an agenda, and produce a briefing.

But a capable LLM may do something quite different. It may decide that it first needs to know who the customer is, discover an available capability, notice that the meeting context is missing, ask a question, change its plan after seeing the answer, and decide that one apparently useful action is unnecessary.

At that point a simple question becomes surprisingly difficult:

**Who made those decisions?**

Did the model already possess the ability to decide at runtime? Did the prompt merely elicit it? Did the tools and context make it possible? Did the system secretly determine the path through orchestration? Or are we looking at a mixture of all four?

And a second question follows.

Suppose the Agent later says:

> “Last week we decided not to contact that customer yet.”

What exactly is being recalled? A stored decision? The original context? A previous conclusion? Or is the model reconstructing a plausible explanation and reasoning about the situation again?

These questions are easy to hide behind a framework. They are harder—and more interesting—to answer before building one.

## The central question

> **Where is the boundary between model capability, system structure, and human cognitive needs?**

The project studies that boundary rather than assuming where it lies.

More specifically:

1. How much Intent-driven Runtime Decision capability does an LLM already possess?
2. When are Prompt, Context, and Tool descriptions sufficient?
3. When does Runtime Decision provide value over predefined Orchestration, and when is explicit control more reliable?
4. What explicit structures, constraints, observations, capability discovery, or persistence mechanisms remain useful when the model can already decide?
5. How can people understand, inspect, challenge, correct, and accumulate Agent decisions?

## A research tension

Modern Agent engineering often moves in two apparently opposite directions.

One direction makes the runtime increasingly explicit: workflows, graphs, routers, planners, state machines, and other forms of orchestration.

The other direction gives the model more freedom: provide an Intent, Context, tools, and capabilities, then let the Agent determine what to do next.

Neither direction is assumed to be correct.

The interesting question is not simply **Runtime Decision vs. Orchestration**. It is:

> **Where should decision control reside, what decision should be made, by whom, and at what point in time?**

This project therefore treats orchestration as an engineering control mechanism rather than an inferior alternative, while treating runtime autonomy as a capability to be measured rather than a design virtue to be assumed.

## Another boundary: Decision and Memory

There is a related problem that appears when an Agent must work across time.

A system can preserve information. It can recall information. It can reason over information. It can make a decision.

Those are not necessarily the same operation.

A useful distinction for this project is:

```text
Preserve → Recall → Reason → Decide
```

The boundaries between these operations are themselves research questions.

For example, a `Decision Archivist` may reconstruct a decision from a complete conversation. That does not mean the Archivist made the decision. Likewise, a later Agent may retrieve that reconstruction and use it as context without merely “remembering” the original cognitive process.

This is why the project studies not only how decisions happen, but also how decisions can be observed, represented, preserved, recalled, questioned, and corrected.

## Research directions

- **A. Intent → Runtime Decision**
- **B. Runtime Decision vs. predefined Orchestration**
- **C. Decision Environment and its observable characteristics**
- **D. Capability Discovery**
- **E. Decision / Alternative / Evidence / Context**
- **F. Memory and Decision boundaries**
- **G. Human-facing representation of Agent Decision**

## What this project does not assume

This project does **not** assume that any of the following must become explicit components of an Agent system:

- Decision Objects
- Decision Environments
- Decision Memory
- Capability Discovery
- Decision Archives
- explicit Runtime Decision mechanisms
- a new Agent Decision Framework

Their usefulness is something to test.

Likewise, `Decision`, `Alternative`, `Evidence`, and related terms are working analytical concepts. They describe observable behavior or useful external representations; they do not, by themselves, establish that the model contains corresponding discrete internal objects.

## Research principles

- Do not reimplement capabilities the model already has merely because explicit structure is easier to manage.
- Do not confuse observable Agent behavior with an assumed internal model structure.
- Do not assume Runtime Decision or Orchestration is inherently superior; study where decision control belongs and who should exercise it.
- Prefer minimal experiments and ablation/control comparisons before introducing architecture.
- Prefer complete original conversations as research material; avoid selection and summarization that can hide corrections, rejected alternatives, or uncertainty.
- Preserve formation, modification, rejection, preservation, and uncertainty of decisions where observable.
- Preserve Alternatives and Evidence, not only final choices.
- Distinguish **preserve / recall / reason / decide**.
- A Decision Archivist is neutral: it reconstructs and preserves; it does not decide.

## Repository structure

```text
.
├── README.md
├── AGENTS.md
├── rules/
│   └── research.md
├── research/
│   ├── introduction.md
│   ├── terminology.md
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

**Early research / experimental.**

The repository is a research scaffold, not a proposed final Agent architecture.

Start with the [research introduction](research/introduction.md) for the motivation and stories behind the questions, then see [terminology](research/terminology.md) for the project's working vocabulary.