# Evidence — Week 09–10 (Group Phase: Security & Safety in the Nusuk System)

**Course:** CPIT-455 Software Engineering II
**Student:** Amer Bugshan
**Group Project:** Nusuk Crowd Management & Permit Validation System
**My V1 Contribution:** Safety (ALARP) and Security (Cryptographic Validation)

---

## My Individual Role (V1) — written in "I", not "we"

In this iteration of the group project I personally took ownership of the **Safety + Security** part of the dependability strategy. My deliverables were the engineering decisions and the justifications behind them.

### My work — ALARP Safety Principle

- I designed the **ALARP** (As Low As Reasonably Practicable) enforcement layer that prevents over-issuance of Hajj permits beyond the physical capacity of each zone in Makkah.
- I argued that capacity constants must be **hard-coded** and **non-overridable**, so that no administrator — not even for VIP requests — can push more pilgrims into a zone than its safe physical limit.
- I justified this against the failure scenario the team identified (over-issuance leading to crowd-crush), and showed how ALARP eliminates human-judgment errors during high-pressure moments.

### My work — Security & Cryptographic Validation

- I designed the **offline cryptographic validation** scheme: every permit carries an **RSA-2048 digital signature** that gate scanners verify locally, without any network call.
- I specified three security guarantees:
  1. **Digitally Signed Permits** — authenticity provable offline.
  2. **Anti-Forgery Protection** — scanners reject tampered or replayed QR codes.
  3. **Revocation Capability** — the central system can mark a permit as revoked, and offline scanners pull the updated revocation list at the next sync.
- I justified RSA-2048 over symmetric schemes because gates must verify without holding any secret key, eliminating the risk of a single compromised scanner leaking the master key.

## How my part connects to the rest of the system

- My **ALARP layer** depends on the *Local Cache* component and the team's *State Desynchronization* failure analysis.
- My **cryptographic layer** is the precondition that makes the team's *Offline-First Reliability strategy* and the *4 R's Resilience framework* trustworthy — without signature verification, "offline" would mean "forgeable."

## Triangulation of Proof (V1)

| Evidence Type | What I produced |
|---------------|------------------|
| Design Evidence  | ALARP enforcement model + RSA-2048 offline validation scheme |
| Process Evidence | This reflection document |
| Runtime Evidence | Pending — to be produced in a later iteration |

— Amer Bugshan · *Build Your Proof.*
