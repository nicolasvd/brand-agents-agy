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

## 2. Calculated Intelligence Layer (ARR & ARM)

The intelligence layer calculates dynamic resonance and algorithmic efficiency metrics. Raw base metrics (followers, views, reactions, comments, shares) remain permanently preserved as empirical ground truth in archives and UI context pills.

### 2.1. Active Resonance Ratio (ARR)
Measures substantive engagement (comments + shares/reposts) relative to superficial one-click reactions (likes, claps, thumbs up):

$$\text{ARR} = \frac{\text{Total Comments} + \text{Total Shares/Reposts}}{\text{Total Reactions}}$$

- **Boundary & Division-by-Zero Guard:** If $\text{Total Reactions} = 0$, evaluate:
  * If $\text{Total Comments} + \text{Total Shares} = 0$, record $\text{ARR} = 0.0\%$ (or `Not applicable` if no posts scanned).
  * If $\text{Total Comments} + \text{Total Shares} > 0$ with 0 reactions (rare edge case), document as pure conversational engagement ($100.0\%$).

| ARR Range | Behavioral Classification | Strategic Interpretation |
|:---:|---|---|
| **$\ge 10.0\%$** | *High Substantive Resonance* | Highly engaged community, deep debate, strong peer-to-peer amplification |
| **$3.0\% - 9.9\%$** | *Healthy Industry Baseline* | Standard commercial engagement, healthy conversational spread |
| **$1.0\% - 2.9\%$** | *Passive Leaning* | Audience consumes primarily in one-click tap mode; low discussion |
| **$< 1.0\%$** | ⚠️ *Severe Passivity / Vanity Reach* | Presumption of severe comment pre-moderation, ad-blindness, or fake likes |

### 2.2. Algorithmic Reach Multiplier (ARM)
Measures organic video distribution power by comparing average video/reel views to the brand's baseline follower community:

$$\text{ARM} = \frac{\text{Average Video Views}}{\text{Total Followers}}$$

- **Boundary & Division-by-Zero Guard:** If $\text{Total Followers} = 0$ or if the channel has zero video publications (e.g. text/image-only channel), document $\text{ARM} = 0.0\times$ or `Not applicable` with an explicit note. Do NOT divide by zero.

| ARM Range | Behavioral Classification | Strategic Interpretation |
|:---:|---|---|
| **$\ge 2.0\times$** | *Algorithmic Breakout* | Proven capability to break through algorithmic feed barriers beyond followers |
| **$0.5\times - 1.9\times$** | *Healthy Base Distribution* | Normal platform distribution matching or slightly under current audience size |
| **$< 0.2\times$** | ⚠️ *Subdued Distribution* | Content fails to gain organic traction; heavy algorithmic friction |

### 2.3. Brand Conversational Loop Rate
Measures community stewardship and brand conversational responsiveness on substantive comments:

$$\text{Loop Rate} = \frac{\text{Substantive Comments with Official Brand Reply}}{\text{Total Sampled Substantive Comments}} \times 100\%$$

- **Boundary Guard:** If $\text{Total Sampled Substantive Comments} = 0$ (e.g. zero comments or comment section disabled), document $\text{Loop Rate} = \text{Not applicable (No substantive comments)}$ and do NOT penalize Pillar 1.
- **Stance Classification:** `Constructive Dialogue`, `Support Deflection`, `Automated Template`, or `Radio Silence`.

---

## 3. Qualitative Confrontation & Tone of Voice Capping

### Semantic Confrontation Protocol
Compare the brand's stated positioning claims (e.g., "Always by your side", "Client-centric innovation") against authentic verbatims collected via `comment-sampling`.

Key indicators to probe:
1. **Support Spillover:** Are users turning public marketing posts into emergency customer support channels?
2. **Brand Responsiveness:** Does the brand acknowledge and resolve negative comments, or maintain `Radio Silence`?
3. **Sentiment Divergence:** Does the visual polish of the post contradict the negative tone of the comments?

### Deterministic Capping Rules
- **ARR Passivity Capping:** If aggregate $\text{ARR} < 1.0\%$, **Pillar 1 (Tone of Voice) is strictly capped at a maximum score of 6.5 / 10** due to vanity reach or severe moderation.
- **Unaddressed Friction Capping:** If the qualitative comment sample contains recurring, unanswered customer support complaints, bugs, or grievances:
  - **Pillar 1 (Tone of Voice) is strictly capped at a maximum score of 6.5 / 10.**
  - An explicit recommendation must be generated in the 4-tier blueprint to address community moderation and customer service integration.
- **Algorithmic Breakout Bonus:** If $\text{ARM} \ge 2.0\times$ on video/reel channels, award a **+0.5 bonus** on Pillar 4 (Content Strategy & Resonance).
