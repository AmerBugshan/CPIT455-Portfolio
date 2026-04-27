# Reflection — Week 02 (Class 01: Domain Spine — Dependable Systems)

**Student:** Amer Bugshan
**Course:** CPIT-455 Software Engineering II
**Date:** April 2026

---

## What I understood

This class established the **Domain Spine** of the whole course:
*Dependability = the degree of trust a user places in a system.*
A dependable system is not "perfect" — it is one that behaves as
expected, with the absence of unwanted behavior, under normal
operation.

The five attributes are not isolated; they are interconnected pillars:

| Attribute    | One-line meaning                                           |
|--------------|------------------------------------------------------------|
| Availability | Ready to deliver service when requested                    |
| Reliability  | Delivers service without failure over time                 |
| Safety       | Avoids catastrophic harm to people or environment          |
| Security     | Protected against accidental or deliberate intrusion       |
| Resilience   | Maintains service under attack or after failure            |

I also learned the **three sources of failure** — Hardware, Software,
and **Operational** — and that *most "system" failures are actually
operational* (human + organizational).

## What changed in how I think

Three ideas reshaped my thinking this week:

1. **Dependability is not free.** The cost-vs-dependability curve is
   exponential. 100 % dependability is infinitely expensive, so an
   engineer's job is to make *justified trade-offs*, not to chase
   perfection.
2. **Redundancy ≠ Diversity.** Two identical servers protect me from a
   hardware failure but **not** from a shared software bug — they will
   both crash on the same input. Diversity (different implementations)
   is what protects against design faults.
3. **Software is socio-technical.** Code does not live in a vacuum. A
   firewall is useless if the operator misconfigures it; a perfect
   algorithm is useless if the business process around it is broken.

## How I applied it (Evidence)

For my portfolio task I picked a real Saudi system — **Nafath**, the
national SSO — and produced a dependability strategy that:

- defines all 5 attributes in the Nafath context,
- identifies hardware / software / operational risks,
- proposes a strategy using **dynamic scaling, microservices,
  diversity, NCA-aligned security, and rapid recovery**,
- ends with an explicit trade-off ranking instead of pretending I can
  achieve 100 % everywhere.

This is exactly the **Triangulation of Proof**:
Design Evidence (the strategy) + Process Evidence (this reflection) +
Runtime Evidence (test cases that come in a later iteration).

## One question for next week

> *"When two diverse implementations of the same authentication check
> disagree, which one wins — and how do we audit that decision so we
> are not just hiding a fault behind a vote?"*

## H-Stack self-check

| H-Stack layer            | Did I show it this week? |
|--------------------------|--------------------------|
| Risk-aware Decision Making  | ✅ Explicit trade-off ranking |
| Evidence-based Reasoning    | ✅ Every strategy tied to an attribute |
| Stakeholder & Socio-technical Thinking | ✅ Considered SDAIA/NCA + ops team |
| Quality & Audit Discipline  | 🟡 Need diagrams + measurable metrics in V2 |
| Ethical Responsibility      | ✅ Ranked Security/Reliability above features |

— Amer Bugshan · *Build Your Proof.*
