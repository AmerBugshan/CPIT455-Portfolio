# Evidence Task 01 — Reliability vs. Availability

**Course:** CPIT-455 Software Engineering II
**Student:** Amer Bugshan
**Week:** 01 — Class 00 (The HIMMA System)
**System (running example for the whole portfolio):** Nafath (نفاذ) — Saudi National Single Sign-On
**Type:** Small Proof (Artifact Evidence)
**Time spent:** ~20 minutes

---

## 1. Clarify (Focused Answer — 5 lines)

- **Reliability** is the *probability* that a system performs its intended function without failure for a specified period of time.
- **Availability** is the *percentage* of time the system is operational and ready to serve a request.
- A system can be **highly available but unreliable** (it is "on" but produces wrong results).
- A system can be **highly reliable but unavailable** (it works correctly when used, but it is offline most of the time).
- The two attributes are related, but **not interchangeable** — each one needs its own metric and its own design strategy.

## 2. Context (Real Example: Nafath / نفاذ)

Consider **Nafath**, the Saudi national Single Sign-On used to log in to Absher, Tawakkalna, banking apps, and dozens of government services.

- **Available but unreliable:** Nafath opens, the login screen loads, the user receives the push notification — but tapping "Approve" returns the wrong status (e.g., approval is recorded but the relying app is told "rejected"). The system is *up* but it produces wrong results, so the citizen cannot complete their transaction.
- **Reliable but unavailable:** Nafath works perfectly, but it is taken offline every night from 2 AM – 4 AM for maintenance. A citizen who needs to log in to their bank at 3 AM cannot authenticate.

A dependable national SSO like Nafath must be **both** reliable AND available — especially during peak periods such as Hajj registration, government salary day, or Iqama renewal deadlines.

## 3. Apply (Short Test Case)

| Field         | Value                                                              |
|---------------|--------------------------------------------------------------------|
| Test Case ID  | TC_01                                                              |
| Title         | Successful Nafath approval for bank login                          |
| Pre-condition | Citizen's National ID is registered; Nafath app installed; internet ON |
| Steps         | 1. Enter National ID in bank app  2. Receive push on Nafath  3. Tap Approve |
| Expected      | Bank app receives "approved" status within 5 seconds               |
| Actual (V1)   | Bank app received "approved" status in 3 seconds                   |
| Status        | **Pass**                                                           |

This single test case is **artifact evidence** that Nafath was *reliable* on this run. Repeating the request 1000 times and counting failures would produce **POFOD** (Probability Of Failure On Demand) — a true reliability metric. Logging total uptime over a month would give the **Availability %** (e.g., 99.95 % SLA).

---

## 4. Concept Map (Simple Diagram)

```
            +------------------+
            |   DEPENDABILITY  |
            +--------+---------+
                     |
       +-------------+-------------+
       |                           |
+------v-------+           +-------v------+
| RELIABILITY  |           | AVAILABILITY |
| "works right"|           |  "is up now" |
| metric: POFOD|           |  metric: %   |
+--------------+           +--------------+
```

## 5. Link to HIMMA

This task is my **first Small Proof**. It is not a massive project — it is 5 clear lines, a real Saudi-context example (Nafath), one test case, and one diagram. That is exactly what the HIMMA "Evidence = Clear Thinking" policy asks for. **Nafath will remain my running example for the rest of the portfolio**, so each week's evidence builds on the previous one.

— Amer Bugshan
