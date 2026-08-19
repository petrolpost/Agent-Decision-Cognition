# Experiments

Experiments are the primary mechanism by which this project decides whether explicit Agent Decision structures are necessary.

## Experiment Template

Each experiment should, where applicable, record:

1. **Question** — the precise behavior under investigation.
2. **Hypothesis** — what we expect and why.
3. **Baseline** — the simplest condition that can answer the question.
4. **Controlled change** — what is added or removed between conditions.
5. **Corpus / Task** — preferably complete, naturally occurring material when studying conversations.
6. **Observation** — what actually happened.
7. **Finding** — what the observation supports or contradicts.
8. **Alternative explanations** — what remains unresolved.
9. **Next experiment** — the smallest useful follow-up.

## Preferred Experiment Pattern

```text
Baseline
   ↓
One controlled change
   ↓
Observe
   ↓
Compare
   ↓
Finding
```

Avoid introducing a framework, schema, or new Agent component before simpler baselines have been tested.

## Existing Research Threads

- `intent-runtime-decision/`
- `runtime-vs-orchestration/`
- `decision-environment/`
- `capability-discovery/`
- `decision-memory/`
- `human-facing-representation/`

These directories may remain empty until a concrete experiment begins.
