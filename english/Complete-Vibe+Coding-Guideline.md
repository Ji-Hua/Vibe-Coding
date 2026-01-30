# Vibe + Coding: A New AI Coding Paradigm

## Introduction

Vibe Coding is a very powerful tool.

As an engineer who has spent many years designing and maintaining systems, I am genuinely happy to adopt any technology that can reduce implementation labor. AI is clearly one of the most promising among them.

However, after nearly a year of real-world usage, I gradually realized a hard truth:

**AI cannot independently take responsibility for implementing medium-to-large-scale systems.**

Even in moderately complex projects, it is very easy for AI-generated code to drift into structural collapse, semantic deviation, and long-term unmaintainability.

These problems rarely manifest as “the code doesn’t run.”
Instead, they surface at the engineering quality level, for example:

- Writing code unrelated to the original design goals
- Hardcoding values that should have been passed via parameters or configuration
- Randomly adding meaningless logs or debug output
- Defining confusing function interfaces with unclear responsibilities
- Expanding inheritance hierarchies arbitrarily, without abstraction boundaries
- Modifying project directory structures at will
- Installing dependencies without constraint, introducing hidden complexity

I tried more complex prompts, stricter instructions, and even step-by-step agent decomposition.
The results were still limited.

Under this mode, AI can at best handle simple, local, low-risk implementations.
Once task complexity increases, the entire project quickly spirals out of control.

The real turning point came from an ordinary personal project.

I wanted to implement a board game as a web app.
Unlike before, I first wrote the rulebook, then designed test cases based on those rules, and only then started implementing.

At that moment, I suddenly realized:

**The problem was not that AI was insufficiently capable.
The problem was that I had been using it in the wrong way.**

As an engineer with over ten years of experience, I cannot guarantee that every line of my own code is inherently correct.
I rely on documentation to define semantics, tests to constrain behavior, and structure to prevent system decay.

So why would I expect AI to independently complete a complex system without any of those constraints?

AI’s strength is not system design.
Its strength is executing already-made decisions precisely.

Design, trade-offs, judgment, and responsibility ownership are precisely where human engineers provide value.
In other words, project ownership cannot be outsourced to models.

Different engineers naturally produce very different code.
AI is no exception.

After realizing this, I consciously adjusted my workflow:

- First, collaborate with AI to produce design documents, then freeze decisions
- Based on the documents, write tests
- Finally, let AI perform constrained implementation, execution, fixing, and refactoring

I applied this pattern to two projects of different scales, and both largely met my engineering expectations.

At that point, I was confident this was not an accidental success, but a reusable engineering paradigm.

I call this workflow **Vibe + Coding**.

- *Vibe* refers to the design phase
- *Coding* refers to the implementation phase

The two interact only through documentation.

This guide is a systematic consolidation of that paradigm.

---

## Chapter 1｜Design Philosophy

In the introduction, I explained that Vibe + Coding is not a lucky trick, but the result of repeated failures and corrections in real engineering practice.

The purpose of this chapter is to clearly define the **engineering stance and design assumptions** behind this paradigm.

---

### 0. What Is Vibe + Coding (A Precise, Executable Definition)

**Vibe + Coding is not “a smarter form of Vibe Coding.”
It is a forced separation of traditional Vibe Coding into two fully isolated stages.**

These two stages are:

- **Vibe (Design Phase)**
- **Coding (Implementation Phase)**

Their relationship is not mixed collaboration, but **strict responsibility isolation**.

---

### Vibe Phase (Design Phase)

The Vibe phase does exactly one thing:

**Transform the human engineer’s design intent into executable external structures.**

Typical outputs include (but are not limited to):

- Design documents
- Architecture descriptions
- API specifications
- Data structure definitions
- Task specifications
- Behavioral constraints
- Test designs (or testing intent)

In this phase:

- No implementation is pursued
- No syntax details are considered
- No “let’s just write some code to see” is allowed

The sole objective of Vibe is to **freeze decisions and externalize them as documents**.

---

### Coding Phase (Implementation Phase)

The Coding phase also does exactly one thing:

**Implement strictly according to existing documentation and tests.**

In this phase:

- Design is not re-discussed
- No new implicit assumptions are introduced
- No “structural optimizations” are made
- No undocumented behavior is added

Input: documentation
Output: code

---

### A Critical Constraint: No Shared Context

**Vibe and Coding must not share context.**

This is not a recommendation.
It is a **necessary condition for the paradigm to hold**.

This means:

- All information produced in Vibe must be transmitted through documents
- Coding must not rely on “things discussed earlier”
- No implicit communication channel exists beyond docs and tests

At the tooling level, this isolation can be enforced in many ways:

- Different tools (e.g., ChatGPT for Vibe, Cursor or Copilot for Coding)
- Different sessions in the same tool
- Different agent instances with no shared history

**Once context is shared, Vibe + Coding degrades back into old-style Vibe Coding.**

---

### One-Sentence Definition

**Vibe + Coding =
Forcibly splitting Vibe Coding into a “design-to-document” phase and a “document-driven execution” phase,
with strict responsibility separation, isolated context, and communication only via documentation and tests.**

If you cannot do this, you are still using old Vibe Coding.

---

### 1. Two Fundamentally Different Programming Paradigms

### Vibe Coding (Old Paradigm)

In this guide, *Vibe Coding* refers to the most common AI programming workflow today:

- Continuous interaction in a single conversation
- Design, implementation, and debugging mixed together
- AI simultaneously “understands the problem” and “writes the code”
- Engineering continuity depends on implicit conversational memory

This works well for:

- Prototypes
- One-off scripts
- Small utilities
- Exploratory experiments

But in medium-to-large systems, it systematically fails:

- Design intent drifts over time
- Implementation details hijack structure
- Decisions are buried in code and become non-auditable
- When problems occur, it’s hard to explain *why*

This is not a user error or a model weakness.
It is a **structural instability of the paradigm itself**.

Unless explicitly stated otherwise, “Vibe Coding” in this document refers to this old paradigm.

---

### Vibe + Coding (New Paradigm)

**Vibe + Coding is not an enhanced version of Vibe Coding.
It is a structural decomposition of it.**

It forcibly separates:

- **Vibe: design and documentation**
- **Coding: constrained execution**

Responsibilities are isolated, contexts are isolated, and communication occurs only via documents and tests.

The focus is not “how to make AI smarter,” but:

- Who thinks
- Who executes
- How decisions are frozen
- How system semantics are preserved

In this paradigm:

- Humans remain system owners and decision-makers
- AI does not participate in design judgment
- AI exists purely as a **constrained execution role**

Once this separation breaks, the workflow inevitably regresses to old Vibe Coding.

---

### 2. The Real Problem This Paradigm Solves

In real-world software development, engineers rarely spend most of their energy on genuinely hard problems.

Instead, time is consumed by:

- Glue code
- Repetitive structures
- Template logic
- Framework boilerplate
- Engineering noise unrelated to core design

Meanwhile, the parts that truly determine system quality and lifespan—

- Architecture
- Abstraction
- Interface boundaries
- Invariants
- Long-term maintainability

—are often rushed or fragmented.

Vibe + Coding is not about “writing more code faster.”
It answers a more realistic question:

**How can engineers allocate limited cognitive resources to what is truly irreplaceable?**

Thus, it does not pursue efficiency maximization, but:

**Integrity of engineering responsibility.**

---

### No Silver Bullet

**Vibe + Coding is not meant to make programming easy.**

Programming is inherently difficult.
Any narrative claiming “just write better prompts” or “AI can do everything automatically” fundamentally misreads engineering reality.

Vibe + Coding does not reduce thinking.
It does one thing only:

**Reallocate where, how, and by whom thinking happens.**

---

### 3. A Reality That Must Be Faced: Context Is Fragile

At present, all large language models share an unavoidable limitation:

**Context windows are finite and unstable.**

As task scale increases, this limitation systematically emerges:

- Early design decisions are forgotten
- Implicit constraints between modules disappear
- Systems become locally correct but globally wrong
- Root causes become hard to trace

Relying on conversational memory to complete complex engineering work is inherently high-risk.

This is not a model flaw.
It is an **engineering assumption error**.

---

### 4. Core Assumption of Vibe + Coding

Vibe + Coding is built on a clear, restrained assumption:

**AI is not suitable for holding global semantic ownership of complex systems over time.**

Therefore, instead of asking AI to “remember everything,” we must reorganize engineering structure:

- Decompose complex problems into independent tasks
- Provide each task with complete, closed descriptions
- Execute within bounded contexts
- Preserve decisions via documents and tests

Under this structure, AI instability is localized, while humans retain global semantic control.

---

### 5. Documentation Is Redefined

In Vibe + Coding, documentation is not an afterthought.

It is part of the system structure.

Documentation serves as:

- The carrier of design consensus
- The boundary of frozen decisions
- The auditable source of system semantics

It serves three audiences:

- Coding phase execution constraints
- Vibe phase memory anchors
- Your future self

Engineering shifts from continuous conversation to:

**Discrete, versionable, traceable decision sequences.**

---

### 6. Thinking Is Moved Forward, Not Reduced

Vibe + Coding does not reduce cognitive load.

It increases it upfront.

Many decisions previously made “while coding” must now be explicitly resolved, written, and frozen during Vibe.

This is a deliberate trade-off:

- More upfront design effort
- Less low-level implementation labor
- Higher long-term maintainability

If you prefer “just get it running first,” this paradigm may feel uncomfortable.

If you value design-first and test-first engineering, it often brings stronger control.

---

### 7. Scope of Applicability

Vibe + Coding is not universal.

It is best suited for **design-driven problems**, not implementation-driven ones.

When the core difficulty lies in:

- System decomposition
- Stable abstraction
- Clear boundaries
- Long-lived invariants

Design quality matters more than speed.

In contrast, when the core question is:

- Can this be done?
- Is the approach viable?
- Can performance be achieved?

Freezing design early is often inappropriate.

Misuse scenarios are discussed later.

---

### 8. Chapter Summary

Vibe + Coding is neither a shortcut nor a trick collection.
It is an engineering stance:

- Structure over flexibility
- Documentation over memory
- Design over improvisation
- Front-loaded thinking for long-term gain

When engineers focus on *what* and *why*,
and AI focuses on *how under constraints*,
collaboration becomes viable.

This is the core philosophy of Vibe + Coding.

---

## Chapter 2｜Mental Model

Before discussing processes or templates, a correct mental model must be established.
Without it, any workflow eventually degrades back into old Vibe Coding.

**The key is not how you use AI, but how you see yourself and AI.**

---

### 1. A Fundamental Shift: You Are No Longer a “User”

In old Vibe Coding, the relationship is implicit:

- You describe needs
- You explain ideas
- You wait for results

AI is treated as a black box that:

- Understands requirements
- Designs solutions
- Implements code
- Debugs on the side

This relationship is:

**Human requests, AI completes.**

Vibe + Coding breaks this entirely.

You are not:

- A tool user
- A prompt engineer
- A requester

You are a:

**Staff Engineer / Tech Lead.**

This means:

- You own system outcomes
- You own architecture quality
- You own long-term maintainability
- You own all critical design decisions

AI is no longer “the one who finishes the work,”
but an **engineering resource you organize and constrain**.

---

### 2. Not One AI, But Three Engineering Roles

Vibe + Coding compresses real team roles into a personal collaboration model.

There are always three roles.

---

### 2.1 You: The Sole System Owner

You own the system.

Your primary job is not writing code, but making judgments:

- What problem to solve
- What not to solve
- Where boundaries lie
- Which abstractions deserve longevity
- Which decisions must be frozen

Your output is not code.
It is **decisions**.

---

### 2.2 Vibe Agent: Design Collaborator

The Vibe Agent participates only in **thinking**.

It helps you:

- Clarify vague ideas
- Decompose complexity
- Surface hidden assumptions
- Propose structured options
- Externalize thought into documents

It is:

- A design discussion partner
- A thinking amplifier
- A high-IQ rubber duck

Critically:

- It has no decision authority
- All conclusions require your confirmation
- It produces candidates, not truth

---

### 2.3 Coding Agent: Constrained Executor

The Coding Agent has a single responsibility:

**Execute strictly according to documentation and tests.**

It may:

- Implement features per spec
- Fix implementations per tests
- Report execution results

It must not:

- Participate in architecture discussion
- Redesign interfaces
- Modify abstraction boundaries
- Introduce undocumented behavior

A strict rule applies:

**The Coding Agent must not make “what seems better” decisions.**

---

### 3. Documentation: Frozen Consensus

Documentation is not:

- Tutorials
- Manuals
- Marketing material

It is:

**Frozen design consensus.**

Think of Vibe as a series of technical meetings.
Documentation is the meeting minutes.

Once frozen:

- Design becomes read-only
- Execution gains stable input

There is no “change code first.”

---

### 4. Tests: Executable Design

In Vibe + Coding, tests are not just quality checks.

They are:

**Executable design contracts.**

- Docs define semantics
- Tests define behavior
- Code implements behavior

If tests fail, either:

- Design is unclear
- Implementation is wrong

Tests are never “too strict.”

---

### 5. A Clear Responsibility Chain

You
↓
Design judgment
↓
Documentation
↓
Tests
↓
Code

Code is always at the bottom.
It never owns meaning.

---

### 6. Failure Starts with Role Confusion

Almost all failures originate from role boundary violations:

- Design during Coding
- Implementation during Vibe
- Coding Agent modifying APIs
- Patching code to hide design flaws

This mirrors real team failures.

---

### 7. Correct Psychological Expectations

Healthy flow feels like:

- Slow but focused Vibe
- Fast, mechanical Coding
- Thinking moved forward
- Lower implementation friction

If you keep fixing design during coding, Vibe was incomplete.

---

### 8. Chapter Summary

In Vibe + Coding:

- You are the owner
- Vibe Agent thinks with you
- Coding Agent executes
- Documentation freezes meaning
- Tests encode behavior

When roles are respected, AI becomes a reliable, auditable execution unit.

---

## Chapter 3｜Methodology – Vibe

After philosophy and mental model comes methodology.

This chapter explains **how Vibe works**, not tools or prompts.

---

### 1. Why Methodology Matters

Old Vibe Coding relies on continuous conversation:

- Decisions hide in context
- State is unrecoverable
- Progress depends on memory

Vibe + Coding converts:

**Continuous dialogue → Discrete decisions**

Only explicit structure enables safe execution.

---

### 2. Four-Stage Model Overview

Vibe uses a fixed four-stage cycle:

**Input → Alignment → Refinement → Freeze**

This model is recursive and reusable.

---

### 3. Input: Declare the Problem, Not the Solution

Input provides a starting point, not answers.

- Vague idea
- Goal description
- Problem statement

No design, no tech choice.

---

### 4. Alignment: Align Understanding, Not Design

Goal: shared understanding of the problem.

- Restate problem
- Clarify scope
- Identify unknowns

No alignment, no design.

---

### 5. Refinement: Turn Problems into Structure

Here you discuss:

- Modules
- Responsibilities
- Data
- Flow

Still no code.

---

### 6. Freeze: Lock Decisions

Freeze means:

- Write it down
- Mark it authoritative
- Execution must follow

New ideas require breaking freeze explicitly.

---

### 7. Fractal Recursion

Apply the same cycle at all scales until tasks become executable units.

---

### 8. Depth-First Progression

Prefer DFS over BFS.

Finish one slice fully before starting others.

---

### 9. Chapter Summary

Input → Alignment → Refinement → Freeze
This is the core of Vibe.

---

## Chapter 4｜Execution Workflow – Coding

This chapter explains how frozen design becomes merged code.

---

### 1. From Freeze to Execution

Design documents are human-readable.
They must be converted into executable tasks.

---

### 2. What Is an Executable Task

If you cannot judge completion objectively, it’s not executable.

---

### 3. Explicit Task Decomposition

Design must be split into atomic tasks.

---

### 4. Test First

Coding starts with tests.

---

### 5. Constrained Execution Loop

Read task → Write tests → Fail → Implement → Pass

No scope expansion.

---

### 6. Implementation Report

Every task must produce an execution report.

---

### 7. Review and Feedback Loop

Audit against documentation, not code aesthetics.

---

### 8. Commit Discipline

One frozen doc version maps to one commit.

---

### 9. Integration Awareness

Integrate early, not at the end.

---

### 10. Refactoring Discipline

Refactor only through documentation changes.

---

### 11. Chapter Summary

Vibe freezes meaning.
Coding executes it.

---

## Chapter 6｜Common Failure Modes and Trade-offs

Failures come from discipline breakdown, not model weakness.

(Sections preserved conceptually as in original.)

---

## Chapter 7｜Conclusion

Vibe + Coding is not about ease or speed.
It is about **control, responsibility, and auditability**.

It separates thinking from execution.
It preserves meaning.
It provides a path to recover from chaos.

That is its value.
