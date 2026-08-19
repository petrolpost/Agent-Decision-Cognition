# Terminology

This document defines how important terms are used within **Agent Decision & Cognition**.

These are working definitions for research, not claims about the internal structure of an LLM or a commitment to a final system architecture.

## Principles

- Terms describe observable behavior, system structure, or research concepts unless explicitly stated otherwise.
- A term becoming useful does not imply that it must become a First Class system object.
- Definitions may change when experiments provide better evidence.
- English terms are retained where they are established technical terms; Chinese explanations clarify their use in this project.

## Core Terms

### Agent — Agent / 智能体

**English:** A system that can pursue an intent by interpreting context, selecting or invoking available capabilities, and taking actions over time.

**中文：** 能够根据意图和上下文，选择或调用可用能力，并持续采取行动的系统。

**Project usage:** The term refers to the system being studied. It does not imply a particular framework, orchestration model, or implementation architecture.

### Intent — 意图

**English:** The goal, purpose, or direction that gives an Agent's runtime behavior its intended orientation.

**中文：** 为 Agent 的运行时行为提供目标、目的或方向的信息。

**Project usage:** Intent is the starting point for studying whether an Agent can determine its own next action at runtime.

### Runtime Decision — 运行时决策

**English:** A choice made during execution about what the Agent should do next, or whether and how it should continue acting, based on the current situation.

**中文：** Agent 在运行过程中，根据当前情况决定下一步做什么、是否继续行动以及如何行动的选择。

**Project usage:** The focus is on where and how decision control occurs, rather than assuming a discrete internal Decision object exists.

### Decision — 决策

**English:** An external description of a choice, change of choice, rejection, preservation, or unresolved choice observable in Agent behavior.

**中文：** 对 Agent 行为中形成、修改、否决、保留或尚未确定的选择进行的外部描述。

**Project usage:** Decision is a working analytical concept. It must not be treated as proof that an LLM internally contains a discrete object with the same structure.

### Alternative — 备选方案

**English:** A possible course of action or option considered, proposed, modified, rejected, or retained in relation to a Decision.

**中文：** 与某个 Decision 相关，被考虑、提出、修改、否决或保留的行动可能性或选择项。

### Evidence — 证据

**English:** Information that supports, contradicts, constrains, or otherwise affects an Alternative or Decision.

**中文：** 支持、反驳、约束或以其他方式影响 Alternative 或 Decision 的信息。

**Project usage:** The project distinguishes externally observed information from model-generated intermediate text. Generated reasoning should not automatically be treated as external evidence.

### Context — 上下文

**English:** Information available to an Agent at a particular point in execution that can influence its interpretation, reasoning, or action.

**中文：** Agent 在特定运行时刻能够获得，并可能影响其理解、推理或行动的信息。

### Decision Environment — 决策环境

**English:** The observable situation in which an Agent makes runtime decisions, including state, constraints, available information, available capabilities, and relevant external conditions.

**中文：** Agent 进行运行时决策时所处的可观察环境，包括状态、约束、可获得信息、可用能力及相关外部条件。

**Project usage:** This is a research concept. The project does not assume that a dedicated Decision Environment component is necessary.

### Memory — 记忆

**English:** Information preserved across time that can be retrieved or made available to influence later interactions or decisions.

**中文：** 跨时间保存，并能够在未来被检索或重新提供，从而影响后续交互或决策的信息。

**Project usage:** Memory is distinguished from the runtime process that originally produced the information. The project explicitly studies the boundary between preserve, recall, reason, and decide.

## Capability and Control

### Capability — 能力

**English:** A function or competence that an Agent can use to accomplish a class of tasks.

**中文：** Agent 可以调用或使用，用于完成某类任务的功能或能力。

**Project usage:** A Capability may be exposed through a Skill, tool, service, or another mechanism. The term does not prescribe the implementation.

### Capability Discovery — 能力发现

**English:** The process by which an Agent identifies capabilities that are available and potentially relevant to its current intent or situation.

**中文：** Agent 根据当前意图或环境，发现可用且可能相关的能力的过程。

**Project usage:** Whether explicit capability discovery provides value beyond prompt, context, or existing runtime capabilities is an empirical question.

### Orchestration — 编排

**English:** Explicitly defining or controlling the sequence, relationships, or routing of actions performed by an Agent system.

**中文：** 由系统显式规定或控制 Agent 行动的顺序、关系或路由。

**Project usage:** Orchestration is treated as an engineering control mechanism, not as an inherently inferior alternative to runtime decision-making.

### Decision Control — 决策控制权

**English:** The locus of authority over who or what determines a particular choice, under what conditions, and at what point in execution.

**中文：** 对某个选择由谁、在什么条件下、于什么时刻作出的控制权。

**Project usage:** This is often a more useful comparison axis than simply asking whether a system is “orchestrated” or “autonomous”.

## Observation and Representation

### Decision Archivist — Decision Archivist / 决策档案员

**English:** A neutral mechanism for reconstructing and preserving Decisions, Alternatives, and Evidence from Agent behavior.

**中文：** 从 Agent 行为中中立地重建并保存 Decision、Alternative 和 Evidence 的机制。

**Project usage:** An Archivist observes and preserves; it is not a Decision Maker and should not steer the Agent toward a preferred choice.

### Human-facing Representation — 面向人的表示

**English:** An external representation designed to help people understand, inspect, question, correct, and accumulate knowledge about Agent decisions.

**中文：** 用于帮助人理解、检验、质疑、修正和积累 Agent 决策信息的外部表示。

**Project usage:** Human-facing representation is a separate concern from the Agent's own runtime decision process.

### First Class

**English:** Having complete, direct, and natural support within a system.

**中文：** 在系统中获得完整、直接、自然的处理能力。

**Project usage:** “First Class” does **not** mean higher priority, higher rank, or more important than other concepts.

## Working / Open Concepts

### Decision Object — Decision Object / 决策对象

**English:** A proposed explicit representation of a Decision for storage, exchange, analysis, or system interaction.

**中文：** 为存储、交换、分析或系统交互而提出的 Decision 显式表示。

**Status:** Open concept. The project does not assume that an explicit Decision Object corresponds to a real internal object in the model.

### Decision Memory — Decision Memory / 决策记忆

**English:** A proposed form of memory concerned specifically with preserving and retrieving information about prior Decisions and their surrounding context.

**中文：** 专门保存和检索历史 Decision 及其相关上下文的信息形式。

**Status:** Open concept. Its necessity and boundary relative to general Memory are subjects for experimentation.

### Cognition — Cognition / 认知

**English:** A broad term for processes associated with interpretation, reasoning, decision-making, learning, and other forms of information processing.

**中文：** 对理解、推理、决策、学习以及其他信息处理过程的统称。

**Status:** Open concept. The project does not assume that human cognitive concepts map directly onto LLM mechanisms.

### Reasoning — Reasoning / 推理

**English:** The process by which an Agent transforms or evaluates available information in order to reach an interpretation, conclusion, or action.

**中文：** Agent 对已有信息进行转换、评估，以形成理解、结论或行动的过程。

**Status:** Working term. It should not be equated automatically with Chain-of-Thought or any particular visible textual trace.

## Related Distinctions

### Preserve / Recall / Reason / Decide

**English:** Four deliberately distinct activities: preserving information, retrieving information, processing information, and selecting an action or outcome.

**中文：** 四种需要刻意区分的活动：保存信息、回忆信息、处理信息以及选择行动或结果。

**Project usage:** The distinction is central to studying the boundary between Memory and Decision.

### Model Capability / Prompt Elicitation / System Structure / Human-facing Structure

**English:** Four factors that should be separated when evaluating an Agent behavior: what the model can do, what the prompt elicits, what explicit system mechanisms provide, and what structures exist primarily for human understanding or control.

**中文：** 评估 Agent 行为时需要区分的四个因素：模型本身具备的能力、Prompt 所诱导出的能力、显式系统结构提供的能力，以及主要服务于人的理解或控制的结构。

**Project usage:** Experiments should attempt to distinguish these factors rather than attributing an observed improvement to “the Agent system” as a whole.
