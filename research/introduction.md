# Agent Decision & Cognition — Introduction

## Why are we asking these questions?

The interesting thing about today's Agents is not that they can call tools.

It is that, increasingly, they can **decide what to do next**.

A user may say:

> “Help me prepare for tomorrow's meeting.”

The user did not specify:

- which documents to read;
- which people to contact;
- whether to search the web;
- whether the calendar matters;
- whether missing information should be requested;
- what should be done first;
- when enough work has been done.

Yet a capable Agent may make all of those choices itself.

That simple observation creates a surprisingly difficult question:

> **How much of what we call an Agent's Decision already exists in the model's runtime behavior, and how much must be explicitly designed into the system?**

This project begins with that question rather than with a framework.

---

## A small story: “Just do what is necessary”

Imagine an Agent connected to a calendar, a document store, email, and a web search tool.

A user says:

> “I have a customer meeting tomorrow morning. Make sure I'm prepared.”

A traditional system might have a workflow:

```text
load meeting
→ find customer
→ retrieve previous notes
→ search recent emails
→ generate briefing
→ return briefing
```

It is reliable because somebody decided the path in advance.

But suppose the Agent discovers that the meeting has been moved to the afternoon. It notices that the latest customer email contains a new issue that is not mentioned in the old notes. It decides that searching the web is unnecessary, but that one internal document is missing. It asks the user for that document instead of continuing with an incomplete briefing.

Now the interesting part is no longer the tool calls.

The interesting part is that **the Agent decided which tool calls mattered**.

Where did that Decision come from?

Was it:

- an implicit capability of the model?
- a consequence of the prompt?
- a property of the available tools and their descriptions?
- a hidden workflow encoded by the system?
- a combination of all of them?
- or something that we are incorrectly describing as a “Decision” after the fact?

We do not want to answer this by choosing a favorite Agent architecture.

We want to find out.

---

## The uncomfortable possibility

There is an easy engineering response to this problem:

> “If the Agent needs to make Decisions, create a Decision module.”

Then perhaps we add a Decision Object, a Decision Engine, a Decision Context, a Decision Memory, and a Decision Orchestrator.

The architecture starts looking increasingly complete.

But something important may have happened without us noticing:

**we have started rebuilding explicitly what the model was already capable of doing implicitly.**

That may be useful in some environments. It may also be unnecessary overhead in others.

The opposite mistake is equally tempting:

> “The model can decide for itself, so explicit system structure is no longer necessary.”

That conclusion is just as premature.

A model may be able to make a good runtime choice while the surrounding system still needs to:

- constrain what it can do;
- expose relevant capabilities;
- provide observations the model cannot obtain itself;
- preserve important prior decisions;
- allow a human to inspect or challenge a choice;
- guarantee behavior where runtime discretion is inappropriate.

So the real question is not:

> **Runtime Decision or Orchestration?**

It is:

> **Where should Decision Control live, and what information, structure, and constraints should surround it?**

---

## Another story: “Why did you decide that?”

Now consider what happens after the meeting.

A week later, the user asks:

> “Why did we decide not to contact the customer last time?”

The Agent searches its memory and finds a summary:

> “We decided not to contact the customer because the issue appeared resolved.”

That sounds useful.

But what exactly has been preserved?

Perhaps the original conversation contained several alternatives:

1. contact the customer immediately;
2. wait for the internal team;
3. request more information;
4. do nothing for now.

Perhaps the Agent initially preferred contacting the customer, then changed its mind after reading a later email. Perhaps the user rejected one proposal. Perhaps the final decision was intentionally left uncertain.

If memory contains only the final sentence, we have preserved an answer but lost the Decision process that made the answer meaningful.

And there is another problem.

Suppose we ask the model today:

> “Reconstruct why you chose option 4 last week.”

It may produce a perfectly coherent explanation.

But is that explanation a memory of the original Decision?

Or is it a new piece of reasoning about an old event?

That distinction is central to this project.

**Recall is not necessarily Reasoning. Reasoning is not necessarily Decision. And preserving a Decision is not the same thing as preserving the information from which the Decision emerged.**

This is why Memory and Decision cannot simply be treated as the same problem.

---

## The strange status of a “Decision”

There is a deeper question underneath all of this.

When we say:

> “The Agent decided to search the email first.”

what exactly are we pointing to?

There may be no discrete object inside the model called `Decision`.

There may be no timestamped internal record saying:

```text
Decision:
    action = search_email
    alternatives = [...]
    evidence = [...]
```

That structure may exist only because **we reconstructed it from observable behavior**.

This does not make the concept useless.

It makes the epistemic status of the concept important.

A Decision Object may be an excellent external representation for humans and systems while still not being a literal description of what happens inside an LLM.

That distinction is one of the reasons this project exists.

---

## From Agent behavior to research questions

These observations lead to a sequence of questions rather than a predetermined architecture.

### 1. Intent → Runtime Decision

If we provide an Intent, Context, and available capabilities, how much can the model decide by itself?

What changes when we add more explicit prompting?

What changes when we add structured context?

What changes when we add Capability Discovery?

And what, if anything, is gained by adding an explicit Decision structure?

### 2. Runtime Decision vs. predefined Orchestration

There are situations where a predefined workflow is clearly appropriate.

There are also situations where the environment is too variable to specify the path in advance.

Rather than arguing about which paradigm is better, we can ask:

> **What characteristics of the Decision Environment make runtime control more useful, and what characteristics make explicit orchestration more reliable?**

### 3. Decision Environment

A Decision never happens in a vacuum.

The Agent sees some information, has access to some capabilities, operates under some constraints, and is exposed to some external state.

How much of the Agent's apparent Decision-making ability comes from the model, and how much comes from the environment we constructed around it?

### 4. Capability Discovery

If an Agent can discover a capability when it needs one, does that provide something fundamentally different from placing all relevant capabilities into its context?

Or are we merely changing how the same information is presented?

This is exactly the kind of question that should be settled experimentally rather than architecturally.

### 5. Decision, Alternative, Evidence, and Context

When reconstructing an Agent's behavior, should we preserve only the final choice?

Probably not.

But if we preserve every intermediate token, we have simply stored the conversation.

The interesting question is whether there is a useful middle ground: an external representation that captures meaningful Alternatives and Evidence without pretending to reveal the model's internal cognition.

### 6. Memory and Decision

What should be preserved?

What should merely be recalled?

What information is needed for a future Decision?

And when does “remembering a previous Decision” become “reasoning again about a previous event”?

### 7. Human-facing representation

Even if an Agent can make Decisions successfully, humans still need to inspect them.

A person may want to ask:

> “Why this option?”

> “What alternatives did you consider?”

> “What evidence mattered?”

> “What were you uncertain about?”

> “Can I reject this Decision?”

The representation needed for those questions may be valuable even when the Agent itself does not need that representation to act.

That is a different engineering requirement, and it should not be confused with model cognition.

---

## Why experiments come before architecture

The project therefore takes a deliberately uncomfortable position:

> **We do not assume that every useful concept needs to become a system component.**

A concept may be:

- a useful analytical vocabulary;
- a human-facing representation;
- an experimental instrument;
- a system capability;
- or ultimately unnecessary.

We want experiments to tell us which one it is.

A useful experiment may therefore be surprisingly small.

For example:

```text
Baseline
    ↓
Intent + Context
    ↓
Intent + Context + Tool descriptions
    ↓
Intent + Context + Capability Discovery
    ↓
Intent + Context + explicit Decision structure
```

If the first condition already produces the behavior we wanted, that is an important result.

It may mean that the additional machinery is unnecessary for that class of problems.

If the behavior becomes more reliable only after explicit structure is added, that is also important.

It tells us something about where the model's capability ends and where system structure begins to matter.

---

## What this project is not trying to prove

This project is not trying to prove that:

- autonomous runtime decision-making is always better;
- predefined orchestration is obsolete;
- LLMs possess human-like cognition;
- Decision is a literal internal object in a model;
- Capability Discovery is always necessary;
- Decision Memory is a new mandatory subsystem;
- one Agent framework is the correct architecture.

Those are conclusions that experiments might support in particular environments, not assumptions we should make at the beginning.

---

## What we are trying to understand

The deeper objective is to locate a boundary.

On one side is **model capability**:

> What can the model already do when given an Intent, Context, and suitable capabilities?

Then comes **system structure**:

> What must the surrounding system explicitly provide, constrain, observe, or preserve?

And finally there is **human cognition**:

> What must be represented so that people can understand, question, correct, and accumulate Agent behavior over time?

These are related, but they are not the same problem.

The project exists to keep them separate long enough to discover where they actually meet.

---

## The guiding question

The most useful question for this project may therefore be the simplest one:

> **What does the Agent already know how to decide, what does the system still need to decide for it, and what does the human need to see even when neither the Agent nor the system needs it to act?**

That question is intentionally open.

We expect some of our current concepts to disappear.

We expect some to become more precise.

We may discover that a mechanism we thought necessary adds almost nothing beyond a better prompt or context.

We may also discover cases where explicit structure is essential.

The goal is not to design the most complete Agent architecture.

The goal is to discover the boundary between **model capability, system structure, and human understanding**.
