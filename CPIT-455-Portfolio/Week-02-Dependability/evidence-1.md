# Portfolio Task: The Dependability Strategy

**Course:** CPIT-455 Software Engineering II
**Student:** Amer Bugshan
**Week:** 02 — Class 01 (Domain Spine: Dependable Systems)
**System:** Nafath (نفاذ) — Saudi National Single Sign-On

---

## 1. Required Dependability Attributes

- **Availability:** Constant access 24/7, since Nafath is the gate to dozens of government and banking services (Absher, Tawakkalna, Tahakkak, bank onboarding, etc.).
- **Reliability:** Every authentication request must return the correct result — no false approvals and no false rejections.
- **Safety:** Protecting citizens from harm caused by identity misuse (e.g., a wrong approval that lets a stranger sign a legal contract).
- **Security:** Safeguarding the national identity database, the OTP channel, and all session tokens against intrusion.
- **Resilience:** The system must keep authenticating users even during partial outages, DDoS attempts, or peak load (Hajj season, Iqama renewal deadlines).

## 2. Risk Identification

- **Hardware:** Authentication servers being saturated during nationwide peak events (e.g., government salary day, Hajj registration window).
- **Software:** Logic bugs in the OTP-generation or token-signing module that approve a request without proper validation.
- **Operational:** Human error inside the SDAIA / NIC operations team — a misconfigured deployment that exposes the API or rotates a signing key incorrectly.

## 3. Proposed Strategy

**Dynamic Scaling & Load Balancing (Availability):** Auto-scale the authentication cluster horizontally during peak hours so that no citizen is locked out of Absher or banking onboarding when traffic spikes.

**Microservices + Independent OTP Service (Maintainability):** Separate the OTP generator, token signer, and identity verifier into independent services so a bug in one can be patched and redeployed without taking the whole SSO offline.

**Diversity over Pure Redundancy (Reliability + Safety):** Run two diverse implementations of the authentication check (different libraries, different data paths). If both must agree before an approval is issued, a single software fault cannot cause a wrong approval — this directly applies the *Redundancy vs. Diversity* lesson from class.

**NCA-Aligned Security Controls (Security):** Enforce mandatory 2FA via OTP, end-to-end TLS, signed JWT sessions, and full audit logging — aligned with **NCA** (National Cybersecurity Authority) and **SDAIA** data-protection standards.

**Rapid Recovery + Read-Only Fallback (Resilience):** If the primary database fails, switch to a read-only replica that can still verify existing identities while writes are queued. This trades a temporary feature loss for keeping the country's services available.

---

## Engineering Trade-Off (The Cost of Perfection)

100 % dependability is infinitely expensive. For Nafath, I prioritize **Security > Reliability > Availability > Safety > Maintainability**, because a single false approval (Reliability/Security failure) damages national trust permanently — which is much costlier than 5 minutes of downtime.

— Amer Bugshan · *Build Your Proof.*
