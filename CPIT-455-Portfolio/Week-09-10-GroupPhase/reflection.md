# Reflection — Week 09–10 (Group Phase: My Role in Nusuk V1)

**Student:** Amer Bugshan
**Group Project:** Nusuk Crowd Management & Permit Validation System
**My V1 Contribution:** Safety (ALARP) and Security (Cryptographic Validation)

---

## What I learned about working in a real team

This was the first time I had to defend an engineering decision in
front of teammates who depend on my part to make their parts work.
The hardest realization was that **my Security work is not a feature
— it is a precondition**. If my RSA signature scheme has a bug, the
whole team's "offline-first" reliability story and the "4 R's"
resilience framework collapse, because "offline validation"
without trustworthy signatures is just a forgeable QR code.

## What changed in how I think

- I stopped thinking "Security = login + password." Security in Nusuk
  means **a signature that can be verified without trusting the
  network**, because in Makkah during Tawaf the network *will* fail.
- I stopped thinking "Safety is a setting." Safety = ALARP =
  **constraints the operator cannot turn off**, even under pressure.
- I now see the 5 dependability attributes as a **chain**, not a
  checklist: my Safety + Security work *enables* the team's
  Reliability + Availability + Resilience claims.

## One question for the group

> *"If a scanner is offline for 12 hours and its revocation list is
> stale, do we fail-closed (reject all permits) or fail-open (accept
> with a warning)? Both choices have a body-count argument."*

## H-Stack self-check (V1)

| H-Stack layer            | This week |
|--------------------------|-----------|
| Risk-aware Decision Making  | ✅ Tied every choice to the over-issuance failure |
| Evidence-based Reasoning    | ✅ Justified RSA-2048 and ALARP against alternatives |
| Stakeholder Thinking        | ✅ Considered gatekeepers, pilgrims, Ministry |
| Quality & Audit Discipline  | ✅ Specified revocation + anti-replay rules |
| Ethical Responsibility      | ✅ Refused VIP-override on capacity limits |

— Amer Bugshan · *Build Your Proof.*
