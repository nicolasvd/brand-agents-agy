---
name: conversational-metrics
description: >-
  Conversational engagement calculation and community resonance auditing skill. Computes conversational ratio, flags audience passivity or heavy moderation, and enforces Tone of Voice capping.
---

# Skill: conversational-metrics

**Role:** Quantitative community engagement evaluator and qualitative sentiment calibrator.  
**Execution Context:** Wave 2 Strategic Analyst (`brand-sub-analyst`).  
**Core Invariant:** Strictly separate surface reactions (likes, claps, thumbs up) from substantive conversation (written comments).

---

## 1. Objectives

- Distinguish passive "scroll-and-tap" audience volume from active community dialogue.
- Quantify audience engagement depth across audited social platforms.
- Enforce the deterministic Tone of Voice (ToV) rating caps when public community feedback reveals unresolved friction.

---

## 2. Conversational Engagement Ratio Formula

Calculate the platform and aggregate Conversational Ratio across extracted post sets:

$$\text{Conversational Ratio} = \frac{\text{Total Comments}}{\text{Total Reactions}}$$

### Analytical Interpretation & Alert Thresholds

| Ratio Range | Behavioral Classification | Strategic Interpretation |
|:---:|---|---|
| **$\ge 5.0\%$** | *High Conversational Resonance* | Highly engaged community, healthy debate, active community management |
| **$1.5\% - 4.9\%$** | *Normal Industry Baseline* | Standard commercial engagement, balanced reaction-to-comment spread |
| **$0.5\% - 1.4\%$** | *Low Conversational Activity* | Audience primarily consumes passively; few conversations initiated |
| **$< 0.5\%$** | ⚠️ *Audience Passivity Alert* | Presumption of severe comment pre-moderation, ad-blindness, or superficial vanity reach |

---

## 3. Qualitative Confrontation & Tone of Voice Capping

### Semantic Confrontation Protocol
Compare the brand's stated positioning claims (e.g., "Always by your side", "Client-centric innovation") against authentic verbatims collected via `comment-sampling`.

Key indicators to probe:
1. **Support Spillover:** Are users turning public marketing posts into emergency customer support channels?
2. **Brand Responsiveness:** Does the brand acknowledge and resolve negative comments, or ignore them?
3. **Sentiment Divergence:** Does the visual polish of the post contradict the negative tone of the comments?

### Deterministic Capping Rule
- If the qualitative comment sample contains recurring, unanswered customer support complaints, bugs, or grievances:
  - **Pillar 1 (Tone of Voice) is strictly capped at a maximum score of 6.5 / 10.**
  - An explicit recommendation must be generated in the 4-tier blueprint to address community moderation and customer service integration.
